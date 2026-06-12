---
title: "Unresolved ARP-Query (avahi related?)"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by manties on 2007-12-29
I am using Ubuntu 7.10 and when statring firefox I have a strange problem. The first few queries to a website are resolved properly. However, after a some time (a few seconds up to one minute) the pages will not be displayed anymore. Running wireshark shows me, that my client machine sends ARP-Requests to the local dns-server (standard Gateway) which are not replied anymore. The ARP-Requests stay unaswered which means that no communication over another protocol can be made. The client is busy sending ARP requests. Could this be a problem related to avahi? In the version 5.04 I did not have this problem. It appeared since version 06.06

I tried to edit /etc/nsswitch.conf, including the line

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

since I thought it could have to do something with AVAHI. This did not help. Any idea what i need to do in order to have the ARP-Requsets resolved.

---

### Post by spd106 on 2007-12-30
MDNS (Avahi) will only be used for domains ending in .local and only on the local LAN. So if you don't have any other machines using MDNS you can disable or remove avahi-daemon without any side effects. Or simply remove the mdns parts from the resolv.conf. 

You should then be able to eliminate it as a source of the problem.

---

### Post by manties on 2008-01-02
Thank you for the hint. However, my resolv.conf under etc/  looks fine. It has a single entry with the default Gateway. There is nothing related to a mdns entry.

I wanted to simply remove the avahi-deamon. When trying to uninstall "avahi-deamon" there are to many dependencies. The Synaptic Package Manager wants to uninstall "ubuntu-desktop", and then a whole bunch of packages.

1. Is there a way to uninstall all avahi related packages without having to uninstall all these other packages like ubuntu-desktop? I can not imagine that my system will run properly without all these packages.

2. What could be the reason that at first, my ARP-Requests are anwered Properly and after a few minutes, my client will send infinite ARP-Requests to the Gateway (192.168.1.1) which will not tell its MAC-Adress anymore. Because of this, my ARP-cache will empty and the network traffic therfore fails.

---

