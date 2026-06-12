---
title: "two ethernet cards problem getting the firewall/nat to work"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Hugolp on 2007-04-23
Hi

I have a computer with two ethernet cards (eth0 and eth1). Basically eth1 has an static ip (out of the range of the dhcp server) conected to a router that acts as a DHCP server and gives internet acces. eth0 should act as DHCP server for my local network and give internet acces to that network.

Basicalley eth1 -> external network with internet acces, static ip.
                    eth0 -> internal network, should work as DHCP server.

I have internet in eth1 and could make eth0 work as DHCP server. The problem is that there is no way I can get internet in my local network. I know the problems, and I have try to set up a NAT to translate the ip, but no luck.

I installed firestarter as I read it was good for the task. Firestater installs and when I try to configure it as a nat and dhcp server it sais it cant load the firewall. If I disable nat then it works.

I tried guarddog but didnt work. Got mistakes when installing. I tried as well this page [http://ubuntuforums.org/showthread.php?t=91370&highlight=dhcp+nat](http://ubuntuforums.org/showthread.php?t=91370&highlight=dhcp+nat), but didnt work neither.

I just dont know how to get it working.

eth0 (local network)
ip 192.168.80.1
subnet: 255.255.255.1 (tried 255.255.254.0 as well)
gateway 192.168.80.1

eth1 (external network/internet)
ip 192.168.1.251
subnet 255.255.255.0
gateway 192.168.1.1

I am pretty sure the ip and the gateway are set-up as they should. I have no idea what the subnet is, but if I use the same subnet in both (255.255.255.0) internet stops working even in this machine (so no internet from eth1 anymore). If I use a diferent one I get internet from eth1 but no internet to local network).

I tried it in a fresh edgy installation. Anyone can help?

Thanks

Hugo

---

### Post by Hugolp on 2007-04-23
This is very weird. I have been checking what subnet mask is and it just doesnt make sense that I cannot use the same subnet mask in both eth.

The weirdes thing is that if I use 255.255.255.0 in both I lose my internet conection in the server, but if I put 255.255.255.1 in the ethernet of the internal net internent works again in the server, and if I go to network properties and check the values for eth0 and eth1 both show 255.255.255.0, but if I change it to actually those values internet stops.

Can someone explain what is going wrong?

Thanks

Hugo

---

