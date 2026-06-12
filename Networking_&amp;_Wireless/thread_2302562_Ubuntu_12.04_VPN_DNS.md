---
title: "Ubuntu 12.04 VPN DNS"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by savethesquirrels on 2015-11-11
I have a weird issue with DNS when connecting to a VPN. I have set my DNS servers on the VPN connection and wired connection. but when connecting I cannot resolve the local domains. However I can nslookup and resolve them. I'm pretty new to Ubuntu and linux in general and it looks like there is something called dnsmasq or resolvconf doing something since the resolv.conf file shows the name server as 127.0.0.1. How can I get the VPN DNS servers to work?

mike@MikBuntu:~$ ping domain.local
ping: unknown host domain.local


mike@MikBuntu:/etc/NetworkManager/dnsmasq.d$ nslookup
> domain.local
Server:		127.0.0.1
Address:	127.0.0.1#53

Name:	domain.local
Address: 192.168.0.10
Name:	domain.local
Address: 192.168.0.5

I also tried creating a dnsmasq.conf. 
mike@MikBuntu:/etc/NetworkManager/dnsmasq.d$ cat dnsmasq.conf 
#Add entry with .domain and nameserver for forwarding the dns requests for that domain
server=/.domain.local/192.168.0.5
server=/.domain.local/192.168.0.10

mike@MikBuntu:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=28:92:4A:3F:49:85,

[ifupdown]
managed=false

---

