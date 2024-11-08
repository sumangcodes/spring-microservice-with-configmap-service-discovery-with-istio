# spring-microservice-with-configmap-service-discovery-with-istio

# Istio Service Discovery Demo

This repository demonstrates how to set up communication between two microservices using Istio in a Kubernetes environment. It includes exposing services through Istio Gateway, monitoring tools, and visualizing service interactions with Kiali, Prometheus, and Jaeger.

## Prerequisites

To follow along with this demo, you'll need the following:

- A Kubernetes Cluster (e.g., Minikube or a cloud-based service)
- `kubectl` command-line tool
- Istio service mesh installed in the cluster
- Basic knowledge of Kubernetes, Istio, and microservices

## Overview

In this demo, we have two microservices:

1. **Service A**: A REST API that calls **Service B** internally.
2. **Service B**: A REST API that is called by **Service A**.

We use Istio to manage service discovery, load balancing, and routing between the services. Additionally, we expose monitoring tools like **Kiali**, **Prometheus**, **Jaeger**, and **Grafana** for tracking metrics and tracing.

## Steps to Set Up the Demo

### 1. Set Up Kubernetes and Istio

1. **Start a Kubernetes Cluster**:
   - Use a service like Minikube or any cloud provider to create a Kubernetes cluster.

2. **Install Istio**:
   - Follow the Istio installation guide to set up Istio in your cluster and enable automatic injection for Istio sidecars.

### 2. Deploy the Microservices

We have two services (`service-a` and `service-b`). These are deployed using Kubernetes and Istio.

- **Service A** calls **Service B** internally using the internal DNS (`http://service-b.demo.svc.cluster.local:8080`).

### 3. Expose `Service A` with Istio

To allow external access to **Service A**, we expose it using Istio's **Gateway** and **VirtualService** configuration. This ensures that traffic to `http://<istio-ingress-ip>/service-a` is routed to **Service A**.

### 4. Expose Monitoring Tools

We use Istio’s capabilities to expose **Kiali**, **Prometheus**, **Jaeger**, and **Grafana** for monitoring the services.

- **Kiali**: Provides a graphical interface to visualize the service mesh and track interactions.
- **Prometheus**: Collects metrics from the services.
- **Jaeger**: Provides distributed tracing to see how requests flow between the services.
- **Grafana**: Visualizes Prometheus metrics in dashboards.

### 5. Access the Services and Monitoring Tools

Once the services and monitoring tools are set up, you can access them via the Istio ingress gateway:

- **Service A**: `http://<your-istio-ingress-ip>/service-a`
- **Kiali**: `http://<your-istio-ingress-ip>/kiali`
- **Prometheus**: `http://<your-istio-ingress-ip>/prometheus`
- **Jaeger**: `http://<your-istio-ingress-ip>/jaeger`

### 6. Monitoring and Tracing

With this setup, you can track how **Service A** communicates with **Service B**, monitor metrics like request counts, latencies, and visualize the flow of requests across the services using Istio's integrated monitoring tools.

## Conclusion

This demo provides a simple example of how to set up Istio for service discovery and routing, as well as expose monitoring and tracing tools for microservices. The setup can be expanded to include more services and detailed monitoring configurations depending on your needs.

