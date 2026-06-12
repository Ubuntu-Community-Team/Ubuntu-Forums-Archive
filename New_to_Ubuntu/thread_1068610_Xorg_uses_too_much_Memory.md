---
title: "Xorg uses too much Memory"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by theharshone on 2009-02-13
hey, 
After a while of using Kubuntu, xorg starts using ridiculous amounts of memory which slows down my entire system. I have 1.5 GB of RAM and ~2.7 GB swap. Xorg uses like 300MB of memory! Is this a memory leak or bug? How can I minimize Xorg's memory usage. I am not running any compositing software (either compiz or kwin)

---

### Post by itang sanjana on 2009-02-13
it's already been reported as a bug per this [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882) but with no solution? though.

---

### Post by theharshone on 2009-02-16
hmmmm That bug is pretty old. How much memory does Xorg use on your computers?

---

### Post by zika on 2009-02-16
> **theharshone said:**
> hmmmm That bug is pretty old. How much memory does Xorg use on your computers?
one FF window open with two tabs: 450 MiB(virtual)

---

### Post by ShaunByres on 2009-02-16
For some reason, on my previous distro's I have never had any memory leak problem with Xorg.  Is it an update or something causing this problem?

---

### Post by S3NATOR on 2009-02-21
I seem to be having this problem too. I did some searching and it looks like there has been xorg memory leaks in the past but most of the posts I found are from a year or so ago. I'm using both Ubuntu 8.10 32-bit and 64-bit on 2 different PC's. Starting yesterday xorg started taking up massive amounts of memory and swap file. My 64-bit machine has 8GiB of memmory and xorg is now taking up 4.2GB overnight while it sat idle. Both of these PC's recently downloaded some updates. Could there be a bug in one of the updates? How can I go back and see what updates I downloaded? Also, here is a screenshot from my 64-bit machine:

[Link](http://img.photobucket.com/albums/v640/Senator24/PC/memory2.png)

Thanks,
S3N

---

### Post by S3NATOR on 2009-02-25
Sorry for the double post but I figured I should post my findings on my solution. I believe I have narrowed the problem down. Turns out in my case I don't think it has anything to do with Xorg. It just so happens that on the same day on both of my machines I started using a desktop wallpaper slideshow that slowly alternates wallpapers throughout the day using a .xml file. I disabled that and now Xorg has stopped using massive amounts of memory. Hopefully this helps others.


S3N

---

### Post by zika on 2009-02-25
just for sake of (whim)-testing I reverted my machine to open-source video driver (ATI-radeon) from ATI restricted 9.2 and I've seen massive decrease in memory usage by Xorg. and, what is even more important, memory usage is contained regardless of kind of applications and videos etc used ... since I do not use compiz and similar stuff I'm hooked on open-source driver for some time.

---

### Post by theharshone on 2009-02-27
> **S3NATOR said:**
> Sorry for the double post but I figured I should post my findings on my solution. I believe I have narrowed the problem down. Turns out in my case I don't think it has anything to do with Xorg. It just so happens that on the same day on both of my machines I started using a desktop wallpaper slideshow that slowly alternates wallpapers throughout the day using a .xml file. I disabled that and now Xorg has stopped using massive amounts of memory. Hopefully this helps others.


S3N

Hmmm. Interesting. I'll try that and post what happens.

---

