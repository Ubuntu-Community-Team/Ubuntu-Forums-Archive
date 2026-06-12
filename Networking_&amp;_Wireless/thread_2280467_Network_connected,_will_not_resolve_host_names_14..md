---
title: "Network connected, will not resolve host names 14.04.2"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by emoore625 on 2015-05-30
I'm setting up ubuntu 14.04.2 on a virtual machine.  I've set up the machine with a static IP and statically set the /etc/resolv.conf nameserver entries but all host name resolution fails.  Pinging 8.8.8.8 works no issue.  

I've tried setting up the network settings in the GUI and same results.  Could vmware be the issue?  

Pulling hair out of my already bald head, need some help.

---

### Post by papibe on 2015-05-30
Hi emoore625.

Setting manually the resolv.conf don't work so well as the file is recreated after each login (resolvconf package).

You can define your DNS in the /etc/network/interfaces side by side the statics values:
```
dns-nameservers 8.8.8.8  8.8.8.4
```
Also make sure you leave the resolv.conf file as a symlink:
```
$ ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 May 19  2014 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by emoore625 on 2015-05-30
No luck.  Did a fresh install.  DNS-nameservers set as you described.  Even the resolv.conf is identical.

Could it be a web proxy that is shutting me down?

---

### Post by papibe on 2015-05-30
Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
ifconfig

cat /etc/network/interfaces

route -n

arp

cat /etc/resolv.conf 

nm-tool

ps aux | grep dhc

nslookup ubuntuforums.org

dig ubuntu.com

mtr --report -nc1 8.8.8.8
```
Regards.

---

