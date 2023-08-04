# TMC Continuous Delivery Example Using FluxCD

### Only use OPA here.

Flux cli installed in to local computer 

New Cluster
1.  Enable Continuous delivery
    a. UI
    b. CLI - tmc cluster fluxcd continuousdelivery enable --cluster-name <cluster name>
2. k get ns on cluster should look like

tanzu-continuousdelivery-resources   Active   9m9s

tanzu-fluxcd-packageinstalls         Active   8m20s

tanzu-kustomize-controller 

tanzu-source-controller

k get pods -n tanzu-kustomize-controller
and
k get pods -n tanzu-source-controller

3. Add ssh credntials for their lab

4. Add git repo
name: tmc-cd
url: https://github.com/ydaoqi/tmc-cd.git

5. Add Kustomization
repo is tmc-cd 
path /continuous-delivery/psp/flux-config
turn prune on

check "addons" tab to see new stuff

<find the logs way to watch>

### Force CD to sync with git repo
```
flux reconcile source git livefire-tmc -n tanzu-continuousdelivery-resources
```
### Force CD to apply changes seen in git repo
```
flux reconcile kustomization flux-deploy -n tanzu-continuousdelivery-resources
```
