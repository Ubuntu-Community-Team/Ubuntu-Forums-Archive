---
title: "iproute and arpd"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by gabogabo on 2007-06-11
I'm installing Honeyd on my pc and I'm reading this guide :
[http://www.securityfocus.com/infocus/1659](http://www.securityfocus.com/infocus/1659)
in order to use unused ip address of my network on the Honeyd I have to submit this two command 

arpd 192.168.1.0/24
 
honeyd -p nmap.prints -f honeyd.conf 192.168.1.0/24

the problem is that I have downloaded the arpd_1.0.2-10_i386.deb but while I was installing it Ubuntu said me the arpd is incompatible with iproute ... :-(

There is a kind of technique in order to submit the same command (arpd 192.168.1.0/24) with iproute or I have to unistall iproute and use arpd ?

---

### Post by elbeeble on 2008-01-11
For anyone who stumbles across this with the same problem. I had the same issue and discovered that arpd is not used anymore. There is a new package called farpd that will accomplish the same thing that arpd did.

---

