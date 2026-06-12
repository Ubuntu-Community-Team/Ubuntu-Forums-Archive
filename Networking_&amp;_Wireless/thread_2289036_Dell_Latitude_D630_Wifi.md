---
title: "Dell Latitude D630 Wifi"
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by positron2 on 2015-07-31
I have a Dell Latitude D630, running Ubuntu 12.0.4, and found that the wireless was not recognized. I researched several times, trying as many solutions that were given, and that I could understand. The solution posted at [http://ubuntuforums.org/showthread.php?t=1865728](http://ubuntuforums.org/showthread.php?t=1865728) worked, but then after rebooting my computer, it once again did not recognize the wireless networks. Help!

---

### Post by riverguy99 on 2015-08-01
We use Dell 620-630 laptops for everything in our office and home.  I used to have all kinds of wifi issues with them until somebody on this forum gave me the simple fix for all of them:  Install the 3945abg wireless card!  They are always available on eBay for as low as $5.  After installing them, our 620-630s found and configured our wifi instantly.  Schweet.

---

### Post by positron2 on 2015-08-03
I will check that out, but I would prefer to keep the existing hardware if possible.

---

### Post by Geoffrey_Arndt on 2015-08-03
What wireless network card/chipset do you have?   Are you running Intel a/b/g wireless or Broadcom?

---

### Post by riverguy99 on 2015-08-03
> **positron2 said:**
> I will check that out, but I would prefer to keep the existing hardware if possible.

OK, but I suggest you keep "3945abg" available for when you decide to end your wireless issues with that laptop!  Even when we found a fix for ours it was always temporary.  Replacing the cards meant the end of issues!  It's a five minute job, too.  If you are not familiar with the process, just do "replace wireless card dell d-620" on Youtube for a good how-to video.  Here's one on eBay for $4.93 with free shipping ; [http://ebay.to/1MHYjBh](http://ebay.to/1MHYjBh)    :D

---

### Post by positron2 on 2015-08-04
It is a Broadcom

---

### Post by sandyd on 2015-08-04
> **positron2 said:**
> I have a Dell Latitude D630, running Ubuntu 12.0.4, and found that the wireless was not recognized. I researched several times, trying as many solutions that were given, and that I could understand. The solution posted at [http://ubuntuforums.org/showthread.php?t=1865728](http://ubuntuforums.org/showthread.php?t=1865728) worked, but then after rebooting my computer, it once again did not recognize the wireless networks. Help!

Hi, did you try the command on the last page, i.e.
> **Wild Man said:**
> Please do ```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by positron2 on 2015-09-17
Yes I did. It recognized the wifi card after this, but upon reboot, it would not find any networks.

---

### Post by Kale_Freemon on 2015-09-18
A little bit of a strange idea, but try this and see if it'll maybe work.

When you're wifi is working, go to the terminal and install "gnome-schedule".

> sudo apt-get install gnome-schedule

Then launch it as root.

> gksudo gnome-schedule

Once up, click on new, then click on recurring.

Make it look like what I have in my screenshot.

[ATTACH=CONFIG]264489[/ATTACH]

Then reboot and see if it works.

---

### Post by howefield on 2015-09-18
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by Hadaka on 2015-09-18
Hi, please open a terminal ctrl/alt/t then copy and paste..

```
lspci -nnk | grep -iA2 net
cat /etc/modules
rfkill list all
```
post the output please.

also if you run the suggested /etc/modules file you will append the file with yet another b43
because of the ">>" directive. It will look like this,,

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

b43
b43
b43
b43

```
thanks

---

