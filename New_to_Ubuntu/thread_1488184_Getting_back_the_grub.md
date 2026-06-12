---
title: "Getting back the grub"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by DiegoTc on 2010-05-19
Hi
I have to install windows7 on my laptop, so I lost the grub. So I did the following to have it back.
> 
[LIST]
sudo fdisk -l
[QUOTE]
/dev/sda1 Linux
/dev/sda2 HPFS/NTFS
/dev/sda3 HPFS/NTFS
/dev/sda4 Extendida
/dev/sda5 Kinux swap

$ sudo mount /dev/sda1 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo chroot /mnt   * Here I get an error
> The order <</bin/bash>> can not be execute: Format error executing

[/LIST]
[/QUOTE]

What could the error be?

---

### Post by Darkness Des on 2010-05-19
Is that "*" what you actually typed in or is that to show the comment you put?

---

### Post by wilee-nilee on 2010-05-19
> **DiegoTc said:**
> Hi
I have to install windows7 on my laptop, so I lost the grub. So I did the following to have it back.


What could the error be?

What distro of Ubuntu are you using and do you know if it is grub2 or grub.97

---

### Post by drs305 on 2010-05-19
Hey DiegoTc, 

I'd follow the instructions in one of these two links. The first is for reinstalling Grub after installing another OS.
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")


The second provides instructions for reinstalling Grub2 from the LiveCD. There are several methods - some easier than others. The 'chroot' method is detailed although the ones discussed prior to that method are easier.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by wilee-nilee on 2010-05-19
> **drs305 said:**
> Hey DiegoTc, 

I'd follow the instructions in one of these two links. The first is for reinstalling Grub after installing another OS.
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")


The second provides instructions for reinstalling Grub2 from the LiveCD. There are several methods - some easier than others. The 'chroot' method is detailed although the ones discussed prior to that method are easier.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Good advice.

---

