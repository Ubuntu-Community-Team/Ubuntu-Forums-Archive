---
title: "Newbee HDHomerun+Mythbuntu help"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Bugg25 on 2009-05-21
This is also posted in the HDHomerun forum...
 
I am brand new to the Linux community. I tried KnoppMyth and failed, now I am trying the latest version of Mythbuntu with no luck.
 
I built my first HTPC with the following:
D-Vine 303 case with IRtrans (usb) receiver (not responding)
Asus PQ5-EM mother board with Intel GMA X4500HD onboard video
Intel Pentium E5200 Wolfdale 2.5GHz 2MB L2 Cache LGA 775 65W Dual-Core Processor
4 GB RAM
640 GB hard drive
HDHomerun
 
The machine is working properly (at least Win XP ran fine when loaded). I loaded KnoppMyth and kept getting lost - this was also before I got the HDHomerun. Yesterday I loaded Mythbuntu 9.04 Jaunty Jackalope and was pleased with how much easier it seemed to navigate around in general. I got my HDHomerun in the mail today and have been trying to set it up for sometime now. I have been searching all of the forums and instruction pages and still havent got my system to recognize it.
I downloaded the files and followed the instructions:
*****************************************************
1) Download the latest libhdhomerun from downloads. 
2) Extract and make: 
tar -xzf libhdhomerun_xxxxxxxx.tgz
cd libhdhomerun
make
3) Copy hdhomerun_config to /usr/local/bin/ 
cp hdhomerun_config /usr/local/bin/
4) Discover the HDHomeRun: 
hdhomerun_config discover
 
****************************************
I went to the downloads and got both files (20090415) and followed all instructions, but when I try "hdhomerun_config discover" i get"no devices found"
I have gone through the setup for MythTV (capture cards, etc), I have rebooted, still "no devices found"
 
Can anyone help?

---

