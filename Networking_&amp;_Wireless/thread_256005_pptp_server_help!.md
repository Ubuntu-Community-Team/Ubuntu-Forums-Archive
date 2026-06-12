---
title: "pptp server help!"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by 1oki on 2006-09-12
ok... so i have installed pptpd server, and I am trying to get it working. I edited the config file /etc/pptpd.conf and set the local and remote ips to this:

localip 172.17.0.1
remoteip 172.17.1.1-254,172.17.2.1-254


I added a user to chap like this:

echo "username pptpd password *" >> /etc/ppp/chap-secrets

I added the port 1723 to be forwarded to my server and I can not get a connection from a windows machine... I am able to use pptpconfig to vpn outside my network to a windows machine. But I can not do it vis versa. And these are the same machines, so I know they can connect. I dont have any firewalls on, at least not that I know of. Does Ubuntu have a default firewall? I even tried connecting to my server from my client (both on the same machine) through the localip and i get this message when running in debugmode:

pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernal IP routing table
Destination____Gateway____Genmask____flags___Metric__Ref__Use__iface
192.168.5.0        __ 0.0.0.0_____          255.255.255.0_U______0_____           0____0___        eth0 
0.0.0.0            _____ 192.168.5.1___      0.0.0.0_______             UG         ___ 0______0____0___        eth0




sorry for the underscores... i had to use them so the output would line up correctly!

I think that about covers it... Can someone please help.. I need to connect my two offices together and they use windows... :( Thanks

---

