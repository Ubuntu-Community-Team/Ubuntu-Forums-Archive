---
title: "Where is /etc/sysconfig/network-scripts/ifcfg-eth0?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by blkmax on 2008-05-05
Does anyone know where this file is? There seems to be a lot of posts referring to this, but I can't find it. Even with showing hidden files.

YES,  I'm on the proper Medication!!!


Marc

---

### Post by Monicker on 2008-05-05
That is where Red Hat/Fedora store information about network interfaces.

For debian/ubuntu it is /etc/network/interfaces

---

### Post by blkmax on 2008-05-05
Thanks, I saw this, but all I have in that file is the following, so it did not seem to be the one. My network is running properly. I need to modify my eth0 script file to run the SNORT security software.

auto lo
iface lo inet loopback


Marc

---

### Post by karthikkln on 2010-02-03
in Ubuntu it wont come like on the sysconfig it 'll be like the following

**/etc/NetworkManager/system-connections  **in here go and edit on the ip address and dns or whatever like the network manager front end.,.!!!:D

---

### Post by kumud1973 on 2012-06-27
> **karthikkln said:**
> in Ubuntu it wont come like on the sysconfig it 'll be like the following

**/etc/NetworkManager/system-connections  **in here go and edit on the ip address and dns or whatever like the network manager front end.,.!!!:D
This is a directory and is empty on my linux PC. What are sample files command that used to update the name of PC.
I tried with /etc/hosts and /etc/hostname. But for some reason(?) cmake unable to get the host name. It returns just empty string "".
   while when executiong command host name on bash shell it returns correct name as assigned in /etc/hostname.

Kumud

---

