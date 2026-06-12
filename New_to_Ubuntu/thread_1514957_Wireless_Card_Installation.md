---
title: "Wireless Card Installation"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by jspivey on 2010-06-21
Hello Everyone,
 
Thank you for taking time to read this post from a newbie and thanks again if you have a step by step way of helping me. I've read some of the suggested readings and links but have wound up with good information but nothing that addressees what I am attempting.
 
 
I have a FILEMATE Wireless-N PCI Adapter, Model # 3FMPCIMWN-R, System requirements Win7, Vista, XP, 2K, Linux/Unix that I've inserted into a PCI slot.  The disc with the instructions directs mostly to WIN.  
 
There is some Linux files on the accompanying disc but no instructions of what to do with them.  
Main Folder on disc: Linux Driver
 
Next Folder: Firmware
Inside this folder: RTL8190P
Inside this folder;
boot.img
data.img
main.img
 
Nex Folder: HAL
Inside this folder: rtl8192
Inside this folder a lot of documents that say; C source code and C header
 
Next Folder: ieee80211
Inside this folder a lot of documents that say; C source code and C header and shell script (s)
 
then the following documents:
ifcfg-wlan0-----plain text document
Makefile
RadioPower.sh-----shell script
readme.txt
release_note----VHDL document
runwpa----shell script
wireless-rtl-ac-dc-power.sh----shell script
wlan0dhcp----shell script
wlan0down----shell script
wlan0up----shell script
wpa1.conf-----plain text document
wpa_supplicant-0.5.10.tar.gz----Tar archive (gzip-compressed)
 
 
 
 
Have called the company out in California, got someone on the line.  They e-mailed me an .rar file but without any instructions also.
 
[www.sintecind.com]("http://www.sintecind.com")------
 
I am using this same card with its dual antenna in the WIN machine that has given a steady performance of 48Mbps from a basement location of about 250 ft. from a wireless router.
 
Did see a folder; RTL819xP_Driver
 
In this folder were folders for VistaX64, X86, Win2k,WinX64, WinXP
 
 
So like Larry the cable dude, "I'm tryin to git 'er done"  Kin ya help me?
 
Appreciate yo help,

---

### Post by marshmallow1304 on 2010-06-21
Maybe there are instructions in readme.txt?

---

### Post by OldToker on 2013-03-14
>>BUMP<<

> **marshmallow1304 said:**
> Maybe there are instructions in readme.txt?

There aren't any that are any real help..  I have a mysterious Error 2 when I issue 'make' 

The only thing that I can tell so far is that the package is based on 2.6 kernel & 2.4 kernel.  and my ```
~ $ uname -r
3.5.0-17-generic

``` reveals : 3.5.0-17-generic

So I am quite sure that the problem is fairly easy to fix.. but I lack the proper skills..

---

### Post by 3rdalbum on 2013-03-15
The first step is to see if you can see and connect to your network. If you can, you already have the driver preinstalled on Ubuntu.

---

### Post by QIII on 2013-03-15
Thank you for sharing.  Everyone’s questions and answers are valuable.

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

*Thread **closed.***

---

