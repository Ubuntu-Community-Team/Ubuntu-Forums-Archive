---
title: "virtualBox (or something like it)"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by sethborders on 2009-01-01
HI, I'm a new linux user and I'm currently dual-booting linux and windows vista on my PC.  i was wondering if there is a way to open up windows vista from my main partition while running ubuntu.

---

### Post by theozzlives on 2009-01-01
VirtualBox will work but not so good on 3D graphics.

---

### Post by Copernicus1234 on 2009-01-01
Install it in VirtualBox 2.1. I have both WinXp and the beta version of Win7 running in it without problems. Like the previous guy said, you will not get 3D acceleration though.

---

### Post by NightmareShadow on 2009-01-01
I don't recommend you to use VirtualBox.
It couldn't detect my graphic card and drivers.
And if you have no luck, you can't even enable the Desktop effects. 

Dual Boot is ok, it's slower if you use VirtualBox.

---

### Post by Copernicus1234 on 2009-01-01
> **NightmareShadow said:**
> 
Dual Boot is ok, it's slower if you use VirtualBox.

Isnt this because you didnt allocate enough memory to Vista?

I run WinXP in VirtualBox and its much faster for me compared to  running a "real" version with dual boot.

---

### Post by NightmareShadow on 2009-01-01
> **Copernicus1234 said:**
> Isnt this because you didnt allocate enough memory to Vista?

I run WinXP in VirtualBox and its much faster for me compared to  running a "real" version with dual boot.

Hm, I did. I got 1GB RAM with 4000MB(4GB) paging file.
I had no processes running when I ran Ubuntu in VirtualBox too.

btw, my processor is Intel Core 2 Duo.

---

### Post by albinootje on 2009-01-01
> **sethborders said:**
> HI, I'm a new linux user and I'm currently dual-booting linux and windows vista on my PC.  i was wondering if there is a way to open up windows vista from my main partition while running ubuntu.

VirtualBox is totally awesome in my opinion.

But it will by default work with virtual disks.

Doing a "raw" access to your real Windows partition is tricky, not so easy to do.

Here's a howto for XP :
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

And here's more mentioning some problems with hardware profiles, and the Guest Additions :
[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

Again, I recommend using a virtual disk with a fresh installation. 
(You might have to check your Microsoft License Agreement before doing that ;-)

---

