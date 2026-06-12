---
title: "Grub help please - cannot boot"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by greenwich on 2009-03-11
Hi. I promise I've already tried to help myself by looking at [this thread]("http://ubuntuforums.org/showthread.php?t=24113") but am still stuck, so please help me.

My Grub is corrupt so I can't boot Ubuntu 8.10, only Vista. This is what **sudo fdisk -lu** gives me for the Device Boot, Id and System attributes when I boot from a live CD:

> 
/dev/sda1   27  Unknown
Partition 1 does not end on a cylinder boundary.
/dev/sda2   7   HPFS/NTFS
/dev/sda3   7   HPFS/NTFSCan someone please tell me how I decide which is my Ubuntu partition? If it's /dev/sda1 then I want to do:

> root (hd0,0)
setup (hd0)and then try to reboot and hope I get my Ubuntu back. Does that sound right?

---

### Post by PunkLV on 2009-03-11
While in grup prompt do
```
uuid
```
It's output should be similar to
```
(hd0,0) ext3 \hdd's uid\ - yours ubuntu
(hd0,1) ntfs \hdd's uid\ - Vista
```

Did you install Vista after Ubuntu?

---

### Post by greenwich on 2009-03-11
> **PunkLV said:**
> While in grup prompt do
```
uuid
```
It's output should be similar to
```
(hd0,0) ext3 \hdd's uid\ - yours ubuntu
(hd0,1) ntfs \hdd's uid\ - Vista
```

Did you install Vista after Ubuntu?I did **sudo grub** and then the **uuid** command. I got Error 27: Unrecognized command.

So I went out of grub and back to the live CD command line and tried uuid there. It told me to do

> sudo apt-get install uuidI did that and the error I get is that the uuid package is not available and has no installation candidate.

The laptop came with Vista. I installed Ubuntu via Wubi at Christmas. It got corrupted recently when I had to do a hard shutdown of Windows.

---

### Post by carml on 2009-03-11
> **greenwich said:**
> 
The laptop came with Vista. I installed Ubuntu via Wubi at Christmas. It got corrupted recently when I had to do a hard shutdown of Windows.
If you don't have any important data on Ubuntu,you can reinstall it within Windows or you can download SuperGrub.
I don't know if SuperGrub works with a Wubi-installation of Ubuntu,just try,if doesnt work reinstall.

---

### Post by cariboo on 2009-03-11
From the looks of the output of:

```
sudo fdisk -lu
```

You don't have a Linux partition, how  did you install Ubuntu? On a seperate partition, or inside Windows?

Jim

---

### Post by carml on 2009-03-11
> **cariboo907 said:**
> From the looks of the output of:

```
sudo fdisk -lu
```

You don't have a Linux partition, how  did you install Ubuntu? On a seperate partition, or inside Windows?

Jim
@cariboo907 just read the first post and you find all the answers to your questions ;)

---

### Post by greenwich on 2009-03-12
> **carml said:**
> If you don't have any important data on Ubuntu,you can reinstall it within Windows or you can download SuperGrub.
I don't know if SuperGrub works with a Wubi-installation of Ubuntu,just try,if doesnt work reinstall.I have tried Auto Super Grub. When I booted, it gave me the option to boot into it. It output some memory locations or something, said "Booting..." but then it did nothing further for half an hour, so I had to do another hard shutdown.

I realise now that the How To's I've been reading in this forum are all for normal installs with an Ubuntu partition. I installed via Wubi so I guess I don't have a normal Ubuntu partition.

Are there are Wubi experts here? Looks like I'll have to reinstall Ubuntu from Wubi, but if possible I'd like to find a way to keep my existing Ubuntu files. I only installed at Christmas and I hadn't got round to backing them up yet. Doh!

---

