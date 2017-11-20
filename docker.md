# Docker:
You can run containers in multiple and different networks.
by default a container will be connected to the `bridge` network.

## list networks
`docker network ls`

## create a network:
`docker network create --driver bridge my_new_network`

## connect a container to a network:
You can connect a container to a network at running: `docker run --network=my_new_network my_container`

Or you can connect a container to a network after running: `docker network connect my_new_network`
/!\ The container will be connected to two different networks, the `bridge` by default when we run the container, and
the new network after. If you want to isolated the docker container make sure you disconnect from the default network or
run the container with `--network=none`

## Inspecting:
To check which containers are connected to a network use `docker network inspect my_new_network`

# Annex:
With salt you can use the state `dockerng.network_present` to 1) check and create the network if not present,
2) connect a list of containers to the desired network, (make sure you use `network_mode: null` param if you use the
`dockerng.running` state to run you containers)

