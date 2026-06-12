---
title: "quick question on Gutsy to Hardy Update"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by stoppage on 2009-03-15
Hi, I upgraded from Gutsy to Hardy and after many changes in Xorg.conf, system is stable. 
Problem...boot menu still shows „Ubuntu 7.10 Kernel 2.6.22.16“ 

..$ cat /etc/issue 
Ubuntu 8.04.2 \n \l 

..$ lsb_release -a 
No LSB modules are available. 
Distributor ID:	Ubuntu 
Description:	Ubuntu 8.04.2 
Release:	8.04 
Codename:	hardy 

Can anybody explain what's going on please?

---

### Post by taurus on 2009-03-15
Go into synaptic and remove that old kernel from your system.  Then, edit /boot/grub/menu.lst and remove that entry if it is still there.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by stoppage on 2009-03-15
If I do that, will "Hardy" then come to boot menu automatically? It isn't currently listed in menu.lst....only Kernel 2.6.22.16..and thanks for the prompt reply

---

