---
title: "SSD drive filled up, now fresh install won't boot"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by mikee55 on 2011-04-11
Hi, I have a 32gb OCZ Vertesx solid state drive with 10.10 on it. Last night I got a warning I'm running out of space. Couldn't see how, so after failing to fix, I did a fresh install, 5 times actually, but it won't boot. I keep getting a flashing cursor. I booted my Puppy usb, and wiped the drive. I used the live disk, 10.10, then dropped back to 10.04, then with the live installed I formatted the disk with GParted and re-installed, same thing. Flashing cursor. Looking at the contents on the drive, my install is there?????

Pmount Puppy Drive Mounter says it has 3 partitions

sdb1 ext3 29.2g 24.2G free

So why no boot???

Mike:confused:](*,)

---

### Post by Nickjpost on 2011-04-11
If you want to use 10.04, why not download and install from the 10.04 disc?

---

### Post by mikee55 on 2011-04-11
I want, to use and normally do 10.10. No OS will, installed on the drive, boot! That is my problem. I just get a flashing cursor????

Mike

---

### Post by stoogiebuncho on 2011-04-11
Can you give us more information about the three partitions?  Are they a root partition, a home partition, and swap?

Are you sure that all three partitions were reformatted?

---

### Post by wilee-nilee on 2011-04-11
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by mikee55 on 2011-04-11
Just finally got it back. I removed my other drives, and did an install of Debian. Managed to boot it up to where in text, it asked to log in. Could'nt log in, strange, tried before with this OS and never got to the desktop, but nevertheless, it installed. Again I used 10.04, and finally booted to desktop. I then upgraded to 10.10.

I now worry, will this re-occur? I have a single partition, no swap.

Thanks Mike :)

---

