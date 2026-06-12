---
title: "Dual booting"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by vinzmomma on 2010-06-28
I want to know about Dual Booting my Toshiba Satellite laptop.  
 
OS Name Microsoft Windows 7 Home Premium (32)bit
System Manufacturer TOSHIBA
System Model Satellite L505D
System Type X86-based PC
Processor AMD Athlon(tm) II Dual-Core M300, 2000 Mhz, 2 Core(s), 2 Logical Processor(s)
Installed Physical Memory (RAM) 3.00 GB
Total Physical Memory 2.75 GB
Available Physical Memory 1.73 GB
Total Virtual Memory 5.49 GB
Available Virtual Memory 4.28 GB
Page File Space 2.75 GB

If you can please send a link to point me in the right direction or in text form through e- mail I would appreciate it.

---

### Post by ngrieb on 2010-06-28
I'm dual booting a Toshiba NB305 right now and am using Ubuntu 9.10. It is a fairly simple process. Just create a live disk. Defrag your existing Windows HDD, and use the live disk to partition and install Ubuntu side by side with Windows 7. That's really it. I'll try and find another link, but it really is not that difficult.

---

### Post by wilee-nilee on 2010-06-28
So do you want top do a true dual boot which is separate operating systems, or a wubi install which is Ubuntu inside of Windows?

Have you tried Ubuntu or a Linux Distro before and have you dowloaded a ISO that is burned to a cd?

---

### Post by oldfred on 2010-06-28
Herman has lots of examples on his site, this is one:
Dual Boot win/10.04
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

The install process is esstential the same for windows and Ubuntu. With XP you can use gparted to resize windows, with Vista & 7 it is better to resize with the windows tools. It can all be done as one step in the install but it is better to resize windows and then reboot windows so it can run its chkdsk or other updates to recognize the new size. Then install to the largest unallocated free space.

Since 9.10 installs use grub2 which is real good at finding and setting up for dual booting both windows and Ubuntu.

---

### Post by garvinrick4 on 2010-06-28
Download .pdf file of book, nice read.


[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

