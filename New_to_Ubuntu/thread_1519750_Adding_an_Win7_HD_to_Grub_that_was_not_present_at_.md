---
title: "Adding an Win7 HD to Grub that was not present at install"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Virigoth on 2010-06-28
Hello,

Ubuntu newbie here ^_^.  I initally installed Ubuntu by itself on an independant hard drive, and had my windows HD disconnected (mr saftey installer) and now I would like to reconnect the windows drive but leave the Ubuntu as the default option but have windows available to load.  I've looked at ways to restore GRUB where the installs are on the same partition but I am having trouble figuring out how to do it from two seperate hard drives, especially when the windows drive wasn't present during the initial install.  Any help would be greatly appreciated!

Thanks,

Viri

---

### Post by oldfred on 2010-06-28
Welcome to the forums.

It may make a difference which drive you plug in where. With SATA sda is usually the lowest port and sdb the higher if not port 1 & 2. But BIOS that support SATA let you choose boot drive. Just make sure in BIOS you have the Ubuntu drive booting. 

If IDE primary master will be the boot drive. You set that with cable connection or jumpers on hard drive.

After booting into Ubuntu run this and it should find windows on the other drive.

sudo update-grub

---

### Post by Virigoth on 2010-06-28
This worked! Thanks!

---

