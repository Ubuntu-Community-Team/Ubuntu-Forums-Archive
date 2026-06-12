---
title: "Help with openVPN"
date: 2016-03-29
forum: Networking &amp; Wireless
---

### Post by PWMKzzJ on 2016-03-29
I am trying to get some help with openVPN on my Ubuntu server. I set it all up about a year ago and naturally I only remember about 1/3rd of the process I went through. Since then my server's noip hostname has changed, luckily I quickly figured out that is listed in the .ovpn file and it was easy enough to change. All of my client keys still work but I am still having a problem with the iptables. Basically I have access to my local network resources when the VPN connection is active but no access to the internet. Every time the server reboots I have an issue with the DNS on the clients. I wound up creating a bash script that has all the commands that I need to run after each reboot, however I am looking for a way to make the change permanent.


Here are the commands that seem to fix the issue:


iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A INPUT -i tap+ -j ACCEPT
iptables -A FORWARD -i tap+ -j ACCEPT
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT
iptables-save
service networking restart
service network-manager restart


To be honest Im not even completely sure what all of these commands do. Does anyone know of a way to make this a permanent change?


At some point I am going to have to build another server similar to the way I have my current one setup. My friend has been drooling over the setup I have in my house. Although this time Im going to run OBS and record the entire thing so that I have something to referrence in the future. If someone can recommend a good guide to setting up openVPN from scratch I would appreciate it. I think I used this guide when I set it up for the first time. 


[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04)

---

