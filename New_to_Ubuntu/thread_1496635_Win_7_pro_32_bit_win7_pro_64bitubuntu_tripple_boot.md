---
title: "Win 7 pro 32 bit/ win7 pro 64bit/ubuntu tripple boot"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by samsaptak on 2010-05-29
Hi,
I am new to linux. I want to have a tripple boot with wi7 pro 32bit/ win 7 64 boot pro and ubuntu. The reason i need two win 7 is some softwares i use do not run in in win 7 64 boot.
I want to install all three os in the same hard drive (1tb) and want to keep a second hard drive (1 tb) as a storage which should be accessible from all the os.
My desktop is i7-930, 12 gb ram, 1 gb raedon 5770
I am new to multiboot . So any detailed information regarding partition etc would be extremely helpful.
thanks and regards,

---

### Post by daimaru on 2010-05-29
I am running a ubuntu 10.04 | win 7 64bit gaming | win 7 64bit development system right now. Both windows systems were installed first. Shouldnt matter if you install a 32 and 64 bit system. they are both controlled by the windows boot loader. After installing both windows systems i installed ubuntu. Boot works like this.. i get a grub screen asking me to choose between windows or linux. If i choose windows i get the windows boot loader that lets me choose betseen gaming and development system. 

Partition wise you should keep in mind that you can only have 4 primary partitions on a drive. So you should use an extended partition for linux . I used 1 primary each for my windows systems and 1 extended partition for my ubuntu install. The ubuntu extended partition holds four partitions /boot ;  /home  ; /  ;  and swap of course. Frankly you just need the root partition " / " and swap ... maybe " /home " as an extra but thats about it.

---

