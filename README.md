# mule-4-docker
**Seven Simple Steps to host Mule Runtime on docker**
* Setting up MuleSoft Runtime and Anypoint Clustering on Docker Engine
* Install the docker https://www.docker.com/products/docker-desktop
* Create a simple mule app
* Download standalone mule https://www.mulesoft.com/lp/dl/mule-esb-enterprise 
* Create the docker file
* Run the 5 docker commands 
  # Build image
  1. docker build -t muledockerimage -f DockerFile .
  # Run Docker container
  2. docker run -d -p 8084:8084 --name muleservercontainer1 -i -t muledockerimage
  3. docker run -d -p 8085:8085 --name muleservercontainer2 -i -t muledockerimage
  # Mule server registration with ARM
  Refer https://docs.mulesoft.com/runtime-manager/installing-and-configuring-runtime-manager-agent
  4. docker exec -it muleservercontainer1 /opt/mule/bin/**amc_setup --region eu1 -H 5fd11244-51af-4c75-b72e-3d4cdaab6cf1---39460** mule1
  5. docker exec -it muleservercontainer2 /opt/mule/bin/**amc_setup --region eu1 -H 5fd11244-51af-4c75-b72e-3d4cdaab6cf1---39460** mule2
* On Anypoint Runtime manager create the cluster 
* Deploy the mule sample mule app to the cluster

Reference : 

https://www.mulesoft.com/lp/dl/mule-esb-enterprise

https://docs.mulesoft.com/private-cloud/1.1/installing-anypoint-on-premises

https://www.docker.com/products/docker-desktop

https://docs.docker.com/get-started/overview/
