---
title: "also no sound!"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by furoido on 2010-05-04
Another one with sound problems after upgrading to 10.04!

Not sure if this is relevant...


andrew@andrew-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...
update-rc.d: warning: /etc/init.d/nvidia-kernel missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by madjr on 2010-05-04
you may want to check if the live-cd has the same issue

[http://blog.ibeentoubuntu.com/2010/05/unscrewing-your-failed-ubuntu-1004.html](http://blog.ibeentoubuntu.com/2010/05/unscrewing-your-failed-ubuntu-1004.html)

---

### Post by _0R10N on 2010-05-04
Well, if you already checked that nothing is muted and you're sure is an Ubuntu problem. Then, you should post your alsa conf.

If you have another Linux on your system and you're booting with the GRUB of the other OS, then be sure that you're using the right kernel.

I went through a similar problem, and found out I was working with a previous kernel because I hadn't updated the GRUB (yes, I have another linux on my laptop, and that second GRUB is which boots the system).

Kind regards!

---

