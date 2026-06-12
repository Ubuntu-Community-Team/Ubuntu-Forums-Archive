---
title: "Sharing wireless internet over ethernet to a windows pc help"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by B3DWcYz on 2013-09-20
I have a netbook running ubuntu 12.10 that connects to my wireless internet however all my attempts thus far to try and share this over ethernet to my windows 7 pc have failed. I've tried changing the ipv4 settings under my wired connection on ubuntu to shared with other computers but on my pc it still doesn't recognise the connection and doesn't find any internet access.

Any help would be appreciated, thanks

---

### Post by GwL3eNC on 2013-09-20
Hello,

thats a bit tricky with ubuntu. You need to enable ip forwarding and masquerade with
a firewall script which you can load manual on every startup. I assume you know how
to assign appropriate ip's to both of your lan cards. Make a text file.sh an type in it

#!/bin/bash 
fw="/sbin/iptables"
WWW_IF="wlan0"

LAN_IP="192.168.0.1"
LAN_RANGE="192.168.0.0/24"
LAN_IF="eth0"

echo 1 > /proc/sys/net/ipv4/ip_forward 
$fw -o $WWW_IF -t nat -A POSTROUTING -j MASQUERADE 

you have fo fit the ip and interface settings to yours. using the ifconfig command you
can see some information about your network cards. save the file and make it executeable
with 

chmod u+x file.sh

Then try to start it

sudo ./file.sh

and test if the connection works.

---

