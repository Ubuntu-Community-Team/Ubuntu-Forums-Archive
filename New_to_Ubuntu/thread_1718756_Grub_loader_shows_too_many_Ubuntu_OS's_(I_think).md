---
title: "Grub loader shows too many Ubuntu OS's (I think)"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Longstreet on 2011-03-31
Noob, Apire One D255, Ubuntu 10.10/Win 7 Starter dual-boot. Been using Ubuntu for a couple of days now, with very little problems. I am confused by my boot loader though.

When the loader menu pops up, I have 2 different choices for Ubuntu. It looks something like this:

1. Ubuntu, with Linux 2.6.35-28-generic
2. Ubuntu, with Linux 2.6.35-28-generic recovery mode
3. Ubuntu, with Linux 2.6.35-22-generic
4. Ubuntu, with Linux 2.6.35-22-generic recovery mode

and then what I believe to be the usual recovery and Windows stuff.

Most everything seems to be working fine, but I'm confused. Do I have 2 Ubuntu OS's installed? Why? And if not, what are the extra lines for?

---

### Post by oboedad55 on 2011-03-31
You have two kernels installed, perfectly normal. You can remove the older one if it really bugs you, but I think it's better to leave the older kernel there in case you need to boot into it for some reason, like if you have problems with the newer one. It doesn't take up much space so I would suggest leaving it.

---

### Post by Blasphemist on 2011-03-31
This is a link to instructions for cleaning this up using Synaptic package manager. 
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)
You don't have two versions installed but the kernel that came in the install was replaced and not removed by the upgrade that was done as part of your updates.

---

### Post by Bucky Ball on 2011-03-31
Leave the second one there, leave all as is.

If an update breaks the recent one or you break it tweaking you can boot into the old one. That is the whole idea. ;)

---

### Post by drs305 on 2011-03-31
I'd agree to keep an older working kernel. When the next one comes around, your menu will increase again. At that time you might consider removing the oldest one.

Here is a link on what's happening and how you can remove older kernels when the time comes. I recommend Ubuntu Tweak:
[HOWTO: Remove Older Kernels via GUI (or CLI)]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by Longstreet on 2011-03-31
Ah. That makes sense. I will leave them alone for now, and then clean up later as suggested.

Thanks guys!

---

### Post by Bucky Ball on 2011-04-01
There's another good app for wrangling grub2:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

It rocks. When the next kernel update comes along and you have three kernels and their recoveries on there give it a try. ;)

---

### Post by domu on 2011-04-01
To check what kernels are actually installed in your system (not necessarily the same as listed by grub), you can use my script remove-kernel which is in the 'My Programs' section at [http://www.timedicer.co.uk/]("http://www.timedicer.co.uk/"). Then you can re-run it specifying the kernel(s) you want to delete and, after due warning, they are gone! Example usage:
```
$ sudo /opt/remove-kernel

remove-kernel v.1.0323 (try -h for help)
=============

Debian base   : squeeze/sid
Distro version: Ubuntu 10.04.2 LTS
Grub          : 2 (1.98)
Active kernel : 2.6.32-30-server

Currently installed kernel packages:
linux-headers-2.6.32-30
linux-headers-2.6.32-30-server
linux-image-2.6.32-30-server

No action taken

```

---

