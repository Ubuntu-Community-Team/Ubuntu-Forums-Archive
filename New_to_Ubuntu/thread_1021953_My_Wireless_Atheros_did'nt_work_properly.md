---
title: "My Wireless Atheros did'nt work properly"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by fas143 on 2008-12-26
Hi,
      I entered to ubuntu for some weeks, i connect internet through ethernet cable. am using compaq presario C700 laptop. But its wireless didnt work at all.It contain Atheros AR5007 communication card. i followed some post in forum. but its results nothing. i installed ndiswrapper and found net5211 for installing the driver. when i open ndiswrapper it can see "hard ware present" but the LED didnt blow.

         Also when i press lspci, it displays  "Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)".
         But i look the driver details of wireless in windows vista i found it as Atheros AR5007, and it works properly in windows. 
        


        if any one have the information about this pls help me as soon as possible.

by, Fasil

---

### Post by HertogJan on 2008-12-26
had the same problem yesterday, i intalled madwifi and it instantly worked. Just search on the internet for it. It took me 4 hours yesterday to find this out, but then i finally got it working. Gl with it, and post it if you need more help. I&#314;l gladly help you.

---

### Post by lkraemer on 2008-12-26
Have a look here:
http://ubuntuforums.org/showthread.php?t=792158

It got my Comapq CQ50-139NR Wifi working.

lkraemer

---

### Post by fas143 on 2008-12-26
hi how can install mad wifi

---

### Post by ogechi3emma on 2009-01-16
try this site and reach back on how you feel. 

Presario c700 Wireless Drivers
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34136.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34136.exe)  (or)
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)


:guitar:emma

---

### Post by ogechi3emma on 2009-01-16
XP Drivers for Presario C700

Chipset Drivers:
[http://asia.giga-byte.com/FileList/Driver/motherboard_driver_chipset_intel.exe](http://asia.giga-byte.com/FileList/Driver/motherboard_driver_chipset_intel.exe)

Graphics (Mobile Intel Graphics Media Accelerator X3100 graphics
controller)
[http://downloadmirror.intel.com/14388/a08/win2k_xp14311.exe](http://downloadmirror.intel.com/14388/a08/win2k_xp14311.exe)

Audio Driver: First download and install the UAA driver from the
following link before installing the audio driver:
[http://asia.giga-byte.com/FileList/Driver/motherboard_driver_audio_realtek_azalia.exe](http://asia.giga-byte.com/FileList/Driver/motherboard_driver_audio_realtek_azalia.exe)

After installing this, download and install the audio driver from the
following link:
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34200.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34200.exe)


:guitar:emma

---

