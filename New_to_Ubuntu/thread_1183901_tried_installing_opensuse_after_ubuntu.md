---
title: "tried installing opensuse after ubuntu"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by notransfat on 2009-06-10
I thought I could dual boot 2 version of linux -- ubuntu and open suse -- so I installed opensuse after I had ubuntu up and running fine.  Now neither one will boot.  I am not that interested in opensuse.  I really want to recover my ubuntu installation but I don't know how.  I tried booting with the supergrubdisk cd, as some other posts suggested, but my computer wouldn't boot with it.  I get GRUB Error 21 when I try to boot.  

I can boot with the ubuntu livecd.  I started to reinstall, but I was afraid I would lose my important data so I aborted it.

Any help would greatly be appreciated.  Thanks.

---

### Post by bodhi.zazen on 2009-06-10
How far did you get in the install ?

With the live CD , open gparted and let us look at your partitions.

for general guidance on booting multiple OS see :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Gone fishing on 2009-06-10
I think that after installing opensuse the naming of the partitions changed so that grub cant find the root partition:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

I wonder if you had a flash drive in the USB when you installed Opensuse? You can fix grub by I'd booting from a live CD and fix grub:

Booting the live CD, and from the Terminal type

sudo grub

At the grub promp type

find /boot/grub/stage1

It will tell you where the root partition is something like (hd1,0)
type that in after root

root (hd1,0)

setup (hd0)

quit

Then it should be fixed

Obviously you shoud be able to fix the Opensuse and Ubuntu, I have to say I prefer Ubuntu and I cant get on with KDE 4.1 (I have tried) but if you want to join a domain or authenticate using an ldap nfs server its a lot easier in Opensuse than Ubuntu. If you started to install I'd say you may have broken it so if fixing grub doesnt allow it to boot boot on the live CD or to opensuse and back up you home directory etc in reinstall.

---

### Post by notransfat on 2009-06-11
Thank you very much, gone fishing.  It worked!  I followed your instructions and my pc rebooted without a hitch.  Now I just need to work on understanding what the instructions meant that you gave me.

Thank you, too, bohdi.zazen.  I will use the multi-boot reference you gave me to figure out what in the Sam Hill I'm doing.

---

### Post by Gone fishing on 2009-06-15
Thanks

What it means

Well grub - thats the boot loader program :)
find /boot/grub/stage1 - find the grub boot program for Linux
root (hd0,0) - the boot program is on the first partition of the first hard drive (notegrub counts from 0 upwards also note that grub calls hard drivers hd not sda etc)
setup (hd0) - setup grub on the mbr of the first hard drive, note you could set up grub on a partition such as (hd0,2) this is what I do then use the gag boot loader as I think it easier to change etc.

---

