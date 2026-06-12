---
title: "Netgear WG111v2"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by wheener on 2006-11-04
Hi everyone out there.

This might have been asked b4 but i have purchased a Netgear WG111v2 USB wireless adapter and it does not work i am tempted to use wine to load windows drivers (if it is possible) any advice.

---

### Post by FrodoB on 2006-11-04
The Linux native driver is at the Realtek web site.  It is not the most user friendly install, but I can confirm that it works under EdgyEft.  The led on the device is not used by the driver for visual feedback, and use the make command to create the software.


Select the RTL8187L driver from Realtek's site:
[ftp://61.56.86.122/cn/wlan/rtl8187_linux_26.1010.zip](ftp://61.56.86.122/cn/wlan/rtl8187_linux_26.1010.zip)
If you go to the web site ignore the Debian 3.1 package it will not work in Ubuntu as it is for an older kernel

unzip the driver in your home directory. 

Read the ReadMe.txt file, hear is my take on it:

$ unzip rtl8187_linux_26.1010.zip 

$ Use chmod 755 to make everything in the directory executable:

$ chmod 755 mak*
$ chmod 755 wl*
$ chmod 755 if*

Then make the driver:

$ sudo ./makedrv

Insert the device and see if you see it with iwconfig, if not then run:

$ sudo ./wlan0up 

and you should be able to see the device if you run iwconfig.

Now you have to configure the device and the GUI in:

System -> Administration -> Networking

Seems to work fine. In fact I am sending this message using a WG111 v2 at the moment.

Note that I do not use this device all of the time and I have a lot of confidence in it yet. 

I have also experienced a complete lockup of Ubuntu Linux, which is extremely unusual while using this device, so I suspect that it is not very stable. 

I also, it does not seem to have the stability or lockup issues on Slackware for some reason. I have download the Ubuntu CD using the WG111 v2 on my Slackware machine without any lockup problems. It has locked up Edgy three times in less than 30 minutes. This may be due to the USB hardware in my Ubuntu machine though, so your milage may vary.

I normally use the FD57050 ver3000 or ver4000 which are Ralink and Zydas based devices when I need USB wireless.

See Hendrik-Jan Heins' excellent hardware list for wireless at:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)


Good Luck,

FrodoB

---

### Post by FrodoB on 2006-11-05
Well, I can verify that the WG111G v2 is very stable on Slackware 11.0 after 22 hours and downloading about 8G bytes of information. The ifconfig command does report about 50% dropped packed on the RX, but this appears to be incorrect as the throughput is comparable to wired ethernet and the MD5 checksums do match on the download items.

As stated earlier, it is not stable on my Edgy machine for some reason.

---

