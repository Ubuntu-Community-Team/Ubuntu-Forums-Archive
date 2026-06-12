---
title: "Error when trying to install Ubuntu"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by UneXisted on 2009-05-04
Hello everyone. I'm trying to install Ubuntu with the live cd. After the reboot with Wubi, i chose the option "install". I can choose my language and then i see the the Ubuntu loading screen. So far, so good. But then i see something that i describe as grey artifacts. The top of my screen gives an error message. The bottom of the screen is black.

I cant really use the search, because i cant really describe what i see beause of my poor english. Does anyone know the solution? I really want to try Ubuntu, since i dont like Microsoft.

---

### Post by y_garti on 2009-05-04
first of all you came to the right place second of all you need to check two things
1 is CD errors to see if you download ubuntu correctly
2 is support for your hardware
if you don't have error with the CD try to do a installation without the GUI (its not so hard and you have tons of tutorials on the web)

good luck and tell us what you found

---

### Post by UneXisted on 2009-05-04
> **y_garti said:**
> first of all you came to the right place second of all you need to check two things
1 is CD errors to see if you download ubuntu correctly
2 is support for your hardware
if you don't have error with the CD try to do a installation without the GUI (its not so hard and you have tons of tutorials on the web)

good luck and tell us what you found
I checked the cd for any errors and the cd is working. 

Requirements:
> Recommended minimum requirements
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

700 MHz x86 processor
384 MB of system memory (RAM)
8 GB of disk space
Graphics card capable of 1024x768 resolution
Sound card
A network or Internet connection
Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation.
Im sure my computer can handle Ubuntu. I took the x86 version with the desktop edition.

I will try the text-based installation (although, im curious why i got to see these artifacts.)

---

### Post by y_garti on 2009-05-04
OK cool keep us inform

BTW do you know what kind of display adepter you've got

---

### Post by UneXisted on 2009-05-05
> **y_garti said:**
> OK cool keep us inform

BTW do you know what kind of display adepter you've got
Ill check it for u.

Im now installing ubuntu via the text installer, but im stuck here. I choose to manual set the partition which i want to install ubuntu on. Ive chosen a free partition, which i have made. The letters K and B are written in the name. Also, i think i have to type a mount point, but i dont know what to type there. I cant continue my installation, without setting a mounting point.

---

### Post by UneXisted on 2009-05-06
Anyone?

---

### Post by UneXisted on 2009-05-06
Anyone?

---

### Post by y_garti on 2009-05-06
what you need is 

/ (the root) with ext3 or ext4 file system
and another is a swap partion with the linx-swap file system

is that answer your question ?

---

### Post by UneXisted on 2009-05-06
> **y_garti said:**
> what you need is 

/ (the root) with ext3 or ext4 file system
and another is a swap partion with the linx-swap file system

is that answer your question ?
So i need three partitions to install Ubuntu?
And i have to give the mountpartitions the following values:
ext3 or ext4
swap

---

### Post by y_garti on 2009-05-06
this will help
[http://img24.imageshack.us/img24/2312/screenshotdevsdagparted.png](http://img24.imageshack.us/img24/2312/screenshotdevsdagparted.png)

---

