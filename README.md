<h1 align="center">
    <strong>Deploying FastAPI Skaffold Application: Deploy your Service in a Single Pod</strong>
</h1>

## Getting started

We'll use of the following tools:

* [minikube](https://minikube.sigs.k8s.io/docs/start/)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
* [Skaffold](https://skaffold.dev/docs/install/)
* [Docker](https://docs.docker.com/get-docker/)

## Usage

Make sure `minikube` is running.

``` bash
minikube start
```

Run `skaffold`, by using the `dev` command.

``` bash
skaffold dev --port-forward
```

Debugging inside the pod.

```bash
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
kubectl exec --stdin --tty $POD_NAME -- /bin/bash
```

Make a request.
```bash
curl localhost:9000
```

And 🎉! Now you're able to debug the campaigns-service inside the running pod.
