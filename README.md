# spree-kubernetes-template

## Usage

### ConfigMaps

There are two minimal configmaps that can be used to pass app-specific environment variables to the containers, such as port numbers etc.
For sensitive data you are best off using a secret, which obfuscates it's content using *base64* encoding.


1. Deployment

`$ kubectl apply -f deployment/config.yml`

2. Migration

`$ kubectl apply -f migration/config.yml`


### Deployment

The deployment resource contains 3 pods along with a *HorizontalPodAutoscaler* that provides basic scaling automation in face of increasing load.
Before deploying you need to set the IMAGE_DIGEST placeholder in the file to match your application's image.

`$ kubectl apply -f deployment/deployment.yml`


### Load Balancer

A basic load balancer preserving the client's IP address is configured. It forwards traffic to port 3000, which is the default port for Spree applications.

`$ kubectl apply -f load_balancer/load_balancer.yml`


### Migration

Before running the migration job set the IMAGE_DIGEST placeholder in the file to match your application's image.

`$ kubectl apply -f migration/migration.yml`
