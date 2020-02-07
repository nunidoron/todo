# TODO helm application

### Solution steps

  - Helm create 
    ```sh
    helm create todo
    ```
  - Enter todo folder:
    ```sh
    cd todo
    ```
  - Edit valuse file, 
    - image set to 'prydonius/todo ' 
    - tagset to '1.0.0'
    - replicas set to 3
    - service type set to "NodePort"
  - Due to pull image error, I'de to change the following param (in todo\templates\deployment.yaml)
    - image: "{{ .Values.image.repository }}:{{ .Chart.AppVersion }}" 
        ".Chart.AppVersion" changed to ".Values.image.tag"
  - Helm install
    ```sh
    helm install todo ./
    ```
  - Ran the followin command
    ```sh
    export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services todo)
    export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
    echo http://$NODE_IP:$NODE_PORT
    ```
  - Ran the followin command
  - checked the web in the relevant address. (image attached to this repo)
  - Create packged for chartmuseum
    ```sh
    helm install todo ./
    ```
  - Helm create package
    ```sh
    helm package .
    ```
  - Due to windown limitations (there is no help push for winsows) I can't uplad to chartmuseum
