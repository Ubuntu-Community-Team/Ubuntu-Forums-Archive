---
title: "How do I fix Modprobe FATAL error report"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by bwallum on 2010-10-22
Hi

A recent upgrade to Maverick has left me an error message at OS boot (just after the GRUB menu) 

The error message is:

Modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory.

The system repeats the error message, waits for a few seconds then goes on to boot normally. Everything appears to run fine but I have later kernels (-26) that are in /lib/modules but do not load. GRUB only lists the -22 version above. My setup is as per my signature.

How do I fix this error?

---

### Post by TeoBigusGeekus on 2010-10-22
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1592311") thread.

---

### Post by bwallum on 2010-10-22
Hole in one, thanks Teo!

Workaround from durlo
#31 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)


In summary:
Open a terminal Applications>Accessories>Terminal
```
gksudo gedit /etc/initramfs-tools/initramfs.conf
```change the line MODULES=most to MODULES=dep

 Then use Synaptic (System>Administration>Synaptic Package Manager) to reinstall initramfs-tools.

---

### Post by TeoBigusGeekus on 2010-10-22
Brilliant! Mark it as solved.

---

### Post by aceja on 2010-11-11
Thanks TeoBigusGeekus, it worked for me..

ASUS UL20FT

---

