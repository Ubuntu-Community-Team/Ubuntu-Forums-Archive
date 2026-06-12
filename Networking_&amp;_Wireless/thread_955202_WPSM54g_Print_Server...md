---
title: "WPSM54g Print Server.."
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by nconceicao on 2008-10-22
Hello Everyone,

I have been trying to figure out how to make my wpsm54g wireless print server to work with Ubuntu.

I've read all the posting tried everything posted and nothing..

Basically I have a laptop 192.168.2.10 and my printer server "wpsm54g" 192.168.2.12

nmap 192.168.2.12

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-10-22 00:08 EDT
Interesting ports on LKA29161 (192.168.2.12):
Not shown: 1712 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
80/tcp open  http


I tried the following
ipp://192.168.2.12:80/ipp/P1 "being that 80 is open"
I tried
ipp://192.168.2.12:631/ipp/P1

Nothing works!

Running Ubuntu 8.04
My printer is a HP 3015
The firmware on the wpsm54g is 1014 "newest is 1017" 
Setup worked Windows
Removed password for wpsm54g "no authentication required"

What am i missing! 

Thanks

---

### Post by patmc13 on 2008-10-23
I am having similar problems with an HP LJ 1320.  I have tried all the things you have as well.  I was able to do it with Ubuntu 6.xx LTS but not on Hardy Heron 8.04 LTS.

---

### Post by patmc13 on 2008-10-23
I found this post:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081)

The post basically says there is a kernel bug that affects Ubuntu 8.04 and Debian Linux.  

basically you need to add the following to  sysctl.conf

To do this
open a terminal and at the command prompt enter

   sudo gedit /etc/sysctl.conf

Insert the new line as:
# Get printing over lan
net.ipv4.tcp_frto = 0

save the file and close the editor. To make the system recognize the change enter the command

   sudo /sbin/sysctl -p /etc/sysctl.conf

I then deleted my printer and re-added it.  I setup my printer as an "Appsocket/HP Jetdirect with my printers IP address and it now works like a charm.

---

### Post by thefinn93 on 2009-02-22
Hello,
I have this print server (WPSM54G) and a Canon MF4150. It's all set up to work with our windows machine, however I am having trouble setting it up on Ubuntu (8.10). It can find it, I did a port scan and came up with several different ports to print on (513, 631 IPP, 9100, 34447 and 34448) as well as two ports to control it on (23 telnet and 80 www), however I cannot seem to get Ubuntu to connect to it. Does anyone have this combination working?

---

