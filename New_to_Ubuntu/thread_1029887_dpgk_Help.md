---
title: "dpgk Help"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Invincibob on 2009-01-03
No idea if this is the right place to post this, but when I try to open Synaptic or use apt-get, I get this message: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So I did what it said and got this:

invincibob@invincibob-laptop:~$ sudo dpkg --configure -a
[sudo] password for invincibob: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-27-386
Cannot find /lib/modules/bootinitrd.img-2.6.15-27-386
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-27-386
dpkg: subprocess post-installation script returned error exit status 1

Synaptic, Add/Remove Applications, and the apt-get commands still don't work, can anyone help?

---

### Post by Michael.Godawski on 2009-01-04
hi,

back up your data :D and try this:

```
sudo dpkg --configure initramfs-tools
```fixed yes, no then do this:
```

sudo update-initramfs -k 2.6.15-27-386 -d
``````
sudo dpkg --configure initramfs-tools
```

---

### Post by Invincibob on 2009-01-04
```
invincibob@invincibob-laptop:~$ sudo dpkg --configure initramfs-tools
[sudo] password for invincibob: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-27-386
Cannot find /lib/modules/bootinitrd.img-2.6.15-27-386
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-27-386
dpkg: subprocess post-installation script returned error exit status 1
invincibob@invincibob-laptop:~$ sudo update-initramfs -k 2.6.15-27-386 -d
Cannot delete /boot/initrd.img-2.6.15-27-386, doesn't exist.
invincibob@invincibob-laptop:~$ sudo dpkg --configure initramfs-tools
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-27-386
Cannot find /lib/modules/bootinitrd.img-2.6.15-27-386
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-27-386
dpkg: subprocess post-installation script returned error exit status 1

```

Still no good. Seemed like it is something that would work, but it won't update that file because apparently I don't have it. Oh, and before I forget, Ubuntu 8.04 if you need my version to help.

---

### Post by Java Geek on 2009-01-04
I just fixed this problem by running the dpgk command and then rebooting. Also you may need to reset your authorizations...

---

