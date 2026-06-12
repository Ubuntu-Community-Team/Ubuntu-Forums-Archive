---
title: "naming my computers"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ginestre on 2009-05-24
Hello again

On my small home net, the mac shows up as mac, the skipe phone as 'skype phone' and until I upgraded from feisty to hardy, the 3 linux machines each had their own names. But on upograde they lost them, and I can't find the place where I can re-set so that I get a nice name on my router rather than an IP number...

TIA for your help

---

### Post by drs305 on 2009-05-24
You can set the name by editing the following files:
```
gksu gedit /etc/hostname /etc/hosts
```
Type the name in /etc/hostname.
> 
mycomputer

Add the hostname in the /etc/hosts file like the following example:
> 
127.0.0.1	mycomputer	localhost
127.0.1.1	mycomputer

The file /etc/hostname is what sets the computer name. The /etc/hosts just updates networking.

---

