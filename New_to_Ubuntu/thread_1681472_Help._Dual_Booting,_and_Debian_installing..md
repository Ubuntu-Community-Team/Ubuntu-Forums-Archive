---
title: "Help. Dual Booting, and Debian installing."
date: 2011-02-04
forum: New to Ubuntu
---

### Post by abnordude on 2011-02-04
Hi, I'm new to ubuntu. But, but being just this far, I'm starting to love ubuntu, that I replaced it with the windows 7 that I had.
As I said, I love ubuntu. And i have also tried installing debian.
But in debian, I experience a problem.
That is, while i'm trying to install debian [through a DVD], it says "no ethernet card". Hence, i cannot connect to the internet. [But, after installing ubuntu, there was no problem & I can connect to the internet].
Then, was the problem of screen resolution ie. in debian.
It was written, "resolution not optimised" or so. And I can't even change the resolution too [I tried to].
I completely uninstalled debian. 
And installed ubuntu.
I'm thinking of dual booting my PC with ubuntu and debian.
But I used all my hard disk space for ubuntu [I hav 500 gb, it's completely for ubuntu]
Is there any partition manager [also maybe defragmenter] for ubuntu that helps me to do this? [Also I don't want to lose my current ubuntu].
Also solve the problem with debian.

---

### Post by cchhrriiss121212 on 2011-02-04
Boot from a live cd and use gparted to set partitions. Debian does not come with a few useful proprietary packages, so I would recommend installing a derivative that does include them. [LMDE]("http://www.linuxmint.com/download_lmde.php") is a good choice.

---

### Post by abnordude on 2011-02-04
> **cchhrriiss121212 said:**
> Boot from a live cd and use gparted to set partitions. Debian does not come with a few useful proprietary packages, so I would recommend installing a derivative that does include them. [LMDE]("http://www.linuxmint.com/download_lmde.php") is a good choice.

I tried using Gparted [Don't know quite well on how to use it], but it says that the whole drive has to be formatted, and I want my current ubuntu to be the same. Is there anyway, that we could divide the partition without affecting the current ubuntu?

---

### Post by Hippytaff on 2011-02-04
LMDE is [linux mint debian]("http://www.linuxmint.com/download_lmde.php") Like mint, which is based on ubuntu, but it's based on debian. (ubuntu is based on debian too) Quite confusing I know.
 
And just to make sur eI understand correctly, you want to dual boot ubuntu with another ubuntu installation?

---

### Post by abnordude on 2011-02-04
> **Hippytaff said:**
> 
 And just to make sur eI understand correctly, you want to dual boot ubuntu with another ubuntu installation?

I want to dual boot, my current ubuntu with debian.
But ubuntu consumes all my hard disk space.
Is there any way to install debian without affecting the current ubuntu [by making use of any partition managers]?

---

### Post by Hippytaff on 2011-02-04
You can try to shrink the ubuntu partition with Gparted frim the liveCD, but back everything up that is important to you because these things can go wrong. If you can post the image from Gparted then we'll have a better idea of what your facing, I say we, my lunch break is almost over, but I'll drop by later.
 
Also be aware, if your planning on installing Debian Lenny be aware that it uses Grub Legacy Bootloader not Grub2. I had fun with this -  [See here]("http://www.suaserve.com/theBlog/?p=62") for details and how I resolved them - if you want, but If you plan on installing squeeze you should be ok because it uses the Grub2 bootloader.

---

### Post by cchhrriiss121212 on 2011-02-04
> I tried using Gparted [Don't know quite well on how to use it], but it says that the whole drive has to be formatted
Was this from a live cd? Formatting the drive will erase all data on there, could you give any more specifics on the message you got?
> Is there anyway, that we could divide the partition without affecting the current ubuntu?
Yes with gparted. You just need to right click on your current Ubuntu partition then select Resize/Move.

---

### Post by jonnny_j22 on 2011-02-04
I usually find it easier to use a seperate gparted live CD.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by oldfred on 2011-02-04
Can be used to shrink or enlarge.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

How many partitions do you have. Have you used all 4 primary?

```
sudo fdisk -lu
```

---

