---
title: "Can't access direct ip docker"
date: 2023-12-27
forum: Networking &amp; Wireless
---

### Post by aftermost2525 on 2023-12-27
I'm running the latest version Ubuntu Server 22.04.3 LTS and have set an static ip 192.168.178.161/24 gw 192.168.178.254.
I've installed docker 24.0.7 with the steps described in the official documentation [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)
Afther that I've created an local network 192.168.180.0/24 gw 192.168.180.254 and deployed an test container witch replies on ICMP with ip 192.168.180.100/24

Now the following situation occurred, on the Ubuntu server itself I can ping 192.168.180.254 and 192.168.180.100. But when doing the same on my client I can ping the gateway from this subnet 192.168.180.254 but I can't ping the container itself via 192.168.180.100. The other way around is working fine from container perspective to the Ubuntu server and client.

If I do an traceroute the path is correct and goes to the gateway 192.168.180.254 but then it stops. 

Can someone give me a hint what are the next logical steps for troubleshooting?

---

### Post by TheFu on 2023-12-27
Most people setup port forwarding from the docker host into the specific service ports of the container.  This is part of the linux container security model.

An answer is provided here: [https://askubuntu.com/questions/1413932/how-do-i-port-forward-from-my-host-to-docker-container](https://askubuntu.com/questions/1413932/how-do-i-port-forward-from-my-host-to-docker-container)
It is part of the docker run command.

There are a few other methods, but I think this is the best.

---

### Post by aftermost2525 on 2023-12-27
I understand that port forwarding is the normal way to go, but for some specific or legacy containers direct ip is the way to go. And i've got this working on an Synology for years but now moving to Ubuntu server and got stuck in my first post. The strange thing is i can access the gateway for the container subnet so the route is should be fine and no firewall is running.

---

