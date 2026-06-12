---
title: "cant access local domain"
date: 2018-11-05
forum: Networking &amp; Wireless
---

### Post by cosy2 on 2018-11-05
> nslookup nas.local                                     
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   nas.local
Address: 192.168.2.6

host nas.local
nas.local has address 192.168.2.6

ping nas.local
ping: nas.local: Name or service not known



i can access the nas via IP, is there any way to do this apart from editing host file?

---

### Post by TheFu on 2018-11-05
Setup the resolv.conf file to point to your DNS server.  In the old days, that would just mean editing the file with an IP address.  Then someone decided to "fix" some problem nobody was having and added a middle-man with the name "resolvconf" ... and move some settings into /etc/resolvconf/.... under there. Think that started around 14.04 (or so) and worked for a few releases.

Then someone else decided to fix another problem nobody had and switch the network controls to something called netplan.  I think that started in 17.10 and later.  

In short, nobody can tell you how to solve the issue within knowing which ubuntu relese you are running and whether you use text config files or some GUI to setup your networking.  For example, I can't help at all with any non-LTS releases after or with any GUI network tools. Basically, I can help with 14.04 or 16.04 text config files only.

---

### Post by cosy2 on 2018-11-05
> **TheFu said:**
> Setup the resolv.conf file to point to your DNS server.  In the old days, that would just mean editing the file with an IP address.  Then someone decided to "fix" some problem nobody was having and added a middle-man with the name "resolvconf" ... and move some settings into /etc/resolvconf/.... under there. Think that started around 14.04 (or so) and worked for a few releases.

Then someone else decided to fix another problem nobody had and switch the network controls to something called netplan.  I think that started in 17.10 and later.  

In short, nobody can tell you how to solve the issue within knowing which ubuntu relese you are running and whether you use text config files or some GUI to setup your networking.  For example, I can't help at all with any non-LTS releases after or with any GUI network tools. Basically, I can help with 14.04 or 16.04 text config files only.
thx for the reply 

i am on 18.10 minimal install, no DE just bspwm

---

