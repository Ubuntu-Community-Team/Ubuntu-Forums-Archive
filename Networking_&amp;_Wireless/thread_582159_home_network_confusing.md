---
title: "home network confusing"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by confusedstingray on 2007-10-19
had linux mint 3.0 up and running network working via samba (windows machines on network)
everything worked with static ips running satellite internet.
previous setup. 

machines  ip=192.168.0.x (x changed from machine to machine)
netmask all machines 255.255.255.0
gateway point to satellite box ip=192.168.0.1 ( all machines gateways pointed to this)

new internet server (faster and cheaper)
windows machines stayed at the ips of 192.168.0.x 
netmask stayed the same 
gatway changed to point to new isp ip of 169.254.1.1
machines run fine and talk to other machines

but the linux machine goes wacky 
static ip 192.168.0.119
netmask 255.255.255.0
gateway 169.254.1.1
it sees the local network but not the internet
if i set it to dhcp it gets a ip of 169.254.1.x changes but most time .2
it sees the internet but not the local network 

i think it has something to do with the bcast settings, if so how do i turn it of 
pretty new to linux have had good results from reading setups, but this is getting 
frustrating, have many years of networking in windows, 
also trying to turn ip6 off 
any help would be great,
thank you for time and patience 
very confuzzed :confused:

---

