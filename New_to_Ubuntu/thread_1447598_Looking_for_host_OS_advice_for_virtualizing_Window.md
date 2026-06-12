---
title: "Looking for host OS advice for virtualizing Windows"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by kgeil on 2010-04-05
Hi, I'm currently looking to begin experimentation using a Linux OS as a host os for virtualizing Windows server, and some Windows clients, in order to do some testing.  If all goes well, I will be considering using a virtualized Windows server in the production environment.  Can someone point me in a good direction to start?  

Specifically, would I be better off using Ubuntu Server, or Ubuntu Desktop (I'd like a gui, but am willing to go without it at some point).

Also, which virtualization software would be best for my needs?

Thanks,

Kevin

---

### Post by Dayofswords on 2010-04-05
you can install a gui on the ubuntu server if you like, gnome, kde, w/e


now for virtulization you can use virtualbox, installable by simple
```
sudo apt-get install vitualbox-ose 
```
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

there also some kind of virtulization through the kernel, no idea on that but here it is
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by new_tolinux on 2010-04-05
> **kgeil said:**
> Also, which virtualization software would be best for my needs?

There's also a non open-source version of VirtualBox, which has more features than the open-source edition (ose).
You can also have a look at VMware.

---

### Post by kgeil on 2010-04-05
Thanks so much for the speedy replies, I'm downloading ubuntu server now.

Kevin;)

---

