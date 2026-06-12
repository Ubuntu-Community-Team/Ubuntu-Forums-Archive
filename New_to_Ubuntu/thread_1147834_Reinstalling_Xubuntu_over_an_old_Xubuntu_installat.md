---
title: "Reinstalling Xubuntu over an old Xubuntu installation"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by INeedMoreSleep on 2009-05-03
I've got a copy of Xubuntu 8.10 running on a Thinkpad t30, and I am trying to reinstall Xubuntu over a previous installation of Xubuntu. I also have a bootable sector with XP that I want to keep in the process. 

If I just stick the installation disk in, will it allow me to overwrite the current Xubuntu installation without a lot of messing around?

Also with my current installation of Xubuntu, the boot screen gives me 7 separate boot options: 

Xubuntu
Xubuntu in safe mode
Xubuntu
Xubuntu in safe mode
Xubuntu
Xubuntu in safe mode
Windows XP

The three separate Xubuntus all seem to take me to the same place, but I was wondering if there was a way to not have the redundancy on the next installation. ( I am quite certain I did not install it three times.)

---

### Post by nandemonai on 2009-05-03
> **INeedMoreSleep said:**
> I've got a copy of Xubuntu 8.10 running on a Thinkpad t30, and I am trying to reinstall Xubuntu over a previous installation of Xubuntu. I also have a bootable sector with XP that I want to keep in the process. 

If I just stick the installation disk in, will it allow me to overwrite the current Xubuntu installation without a lot of messing around?

Also with my current installation of Xubuntu, the boot screen gives me 7 separate boot options: 

Xubuntu
Xubuntu in safe mode
Xubuntu
Xubuntu in safe mode
Xubuntu
Xubuntu in safe mode
Windows XP

The three separate Xubuntus all seem to take me to the same place, but I was wondering if there was a way to not have the redundancy on the next installation. ( I am quite certain I did not install it three times.)

First, those three entries are simply old kernels, not complete installations. You can remove the entries manually from /boot/grub/menu.lst or remove the old kernels all together via synaptic. Just be sure to not remove your current running kernel. You can find out what your running kernel is in terminal with this command:

```
uname -r
```

As for actually installing over the top of xubuntu, that's easily do-able but I wonder if you really want to reinstall or just upgrade?

If you want to retain settings and files in /home/ then upgrade is your best bet (unless you setup a separate /home/ partition).

To install over the top and wipe out the current install you can do manual partitioning in the installer and simply use your current partitions, setting the right mount points and checking to format them.

Really depends how you want to go about it, and what version to what.

Edit:

Just noticed the 8.10 tag. You can do a network upgrade by running this in terminal:

```
update-manager -d
```

---

### Post by INeedMoreSleep on 2009-05-03
Thanks nandemonai, that pretty much covers it.

---

