---
title: "update-grub"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by PeterV007 on 2009-04-18
Hi
Totally new to ubuntu
Trying to setup multiboot with two disks - ubuntu on Master & XP on slave.
Entered"sudo gedit /boot/grub/menu.1st" in order to add new line for XP.Menu.1st was empty. Entered update-grub & received following:

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=1e717e40-c661-4b48-be43-2c7a180d76cd'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied

Any suggestion?

---

### Post by davec64 on 2009-04-18
You want:

```
sudo gedit /boot/grub/menu.lst
```

Its "lst" lowercase L.

---

