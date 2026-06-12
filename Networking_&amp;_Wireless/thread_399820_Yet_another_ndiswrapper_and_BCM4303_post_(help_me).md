---
title: "Yet another ndiswrapper and BCM4303 post (help me)"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by kipling100 on 2007-04-02
Hi everyone,

So I've been working on this for a few days now, and I've followed many tutorials on this site and others, but I'm still having problems, so I thought I'll try my own post before giving up :)

Basically, I'm trying to get my wireless card Linksys WMP11 v2.7 (BCM4303) to work on Ubuntu 6.10.

Here are the background specs:
Kernel version 2.6.17
Ndiswrapper version 1.18 (got this from the LiveCD)
Windows driver for WMP11 3.8.28.0 (release date: 11/15/02)

I started off my blacklisting bcm43xx as per everyone's suggestions, since I want to see if I can use ndiswrapper.

lspci gives:
02:01.0 Network controller: Broadcom Corporation BCM4303 02.11b Wireless LAN Controller (rev 02)

lspci -n gives:
02:01.0 0280: 14e4:4301 (rev 02)

Next, I followed the steps using sudo ndiswrapper -i WMP11V27.inf

This creates the following in /etc/ndiswrapper/wmp11v27:
14E4:4301:1737:4301.5.conf
1434:4301.5.conf
wmp11v27.inf
wmp11v27.sys

ndiswrapper -l gives:
Installed ndis drivers:
wmp11v27       driver present, hardware present

next, I did:
sudo depmod-a
sudo modprobe ndiswrapper

The output of dmesg | grep ndiswrapper shows:
ndiswrapper version 1.40 loaded (smp=yes)
usbcore: registered new driver ndiswrapper

iwconfig gives:
lo   no wireless extensions.
eth0 no wireless extensions.
sit0 no wireless extensions

If i try to bring up wlan0 manually, using sudo ifup wlan0, i get:
SIOCSIFADDR: No such device

If I try to use the Administration > Networking tool, the wireless card doesn't show.

So that is basically it.  I tried doing ndiswrapper -m, and rebooting, with no success.  This is the second WMP11 driver I tried (it is the newest one on the Linksys site, and it is listed in the ndiswrapper compatibility wiki).  Originally, I used the one that came with my card, which is a slightly older version.  Should I be trying a different driver?  

Thanks for any help.  I'm about ready to give up on this thing! :)

Dennis

---

### Post by Floppyjoe on 2007-04-02
> **kipling100 said:**
> Hi everyone,

So I've been working on this for a few days now, and I've followed many tutorials on this site and others, but I'm still having problems, so I thought I'll try my own post before giving up :)

Basically, I'm trying to get my wireless card Linksys WMP11 v2.7 (BCM4303) to work on Ubuntu 6.10.

Here are the background specs:
Kernel version 2.6.17
Ndiswrapper version 1.18 (got this from the LiveCD)
Windows driver for WMP11 3.8.28.0 (release date: 11/15/02)

I started off my blacklisting bcm43xx as per everyone's suggestions, since I want to see if I can use ndiswrapper.

lspci gives:
02:01.0 Network controller: Broadcom Corporation BCM4303 02.11b Wireless LAN Controller (rev 02)

lspci -n gives:
02:01.0 0280: 14e4:4301 (rev 02)

Next, I followed the steps using sudo ndiswrapper -i WMP11V27.sys

This creates the following in /etc/ndiswrapper/wmp11v27:
14E4:4301:1737:4301.5.conf
1434:4301.5.conf
wmp11v27.inf
wmp11v27.sys

ndiswrapper -l gives:
Installed ndis drivers:
wmp11v27       driver present, hardware present

next, I did:
sudo depmod-a
sudo modprobe ndiswrapper

The output of dmesg | grep ndiswrapper shows:
ndiswrapper version 1.40 loaded (smp=yes)
usbcore: registered new driver ndiswrapper

iwconfig gives:
lo   no wireless extensions.
eth0 no wireless extensions.
sit0 no wireless extensions

If i try to bring up wlan0 manually, using sudo ifup wlan0, i get:
SIOCSIFADDR: No such device

If I try to use the Administration > Networking tool, the wireless card doesn't show.

So that is basically it.  I tried doing ndiswrapper -m, and rebooting, with no success.  This is the second WMP11 driver I tried (it is the newest one on the Linksys site, and it is listed in the ndiswrapper compatibility wiki).  Originally, I used the one that came with my card, which is a slightly older version.  Should I be trying a different driver?  

Thanks for any help.  I'm about ready to give up on this thing! :)

Dennis
This part looks wrong to me:
> Next, I followed the steps using sudo ndiswrapper -i WMP11V27.sys
In my experience that command should be done on the .inf file

---

### Post by kipling100 on 2007-04-02
Thanks for your reply...

I actually mistyped that -- I did use the .inf file in the ndiswrapper -i command.

Thanks for pointing that out to me though.

Dennis

---

### Post by Floppyjoe on 2007-04-02
I looked on this site:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) 
and found this info:
> # Card: Broadcom BCM4301 built-in Compaq nx9110 laptop

    * Chipset: Broadcom 4301
    * pciid: 14e4:4301 (rev 02)
    * Driver: Downloaded Windows 2000 driver from Compaq site. FilenameSP28538.exe.
    * Other: Debian with 2.6.8 kernel. NdisWrapper 0.10 built deb and installed. Use bcmwl5.inf. 

# Card: Broadcom BCM4301 built-in HP Pavillion zv5142EA (zv5000 series)

    * Chipset: Broadcom 4301
    * pciid: 14e4:4301 (rev 02)
    * Driver: Downloading latest XP driver for the zv5142EA will surely be ok - as of 2004-10, this is SP27952A. Use driver bcmwl5a.inf here!#*Other: SuSE 9.1 with 2.6.4.52-default kernel. NdisWrapper? installed via YaST. 

# Card: Broadcom BCM4301 built-in HP Compaq nx9010 laptop

    * Chipset: Broadcom 4301 802.11b (rev 02)
    * pciid: 14e4:4301 (rev 02)
    * Driver: bcmwl5.inf from the HP.com Windows XP update file SP28537.exe, using Ndiswrapper 1.1 and wpa_supplicant, everything including WPA-PSK works following installation instructions and using the WPA config file on the wiki. 

# Card: Broadcom BCM4303 built-in HP Pavilion zv5265EA (zv5200 series)

    * Chipset: Broadcom 4303
    * pciid: 14e4:4301 (rev 02)
    * Driver: Works with driver from "Driver Recovery CD" Disc 1 - SWSetup/WLAN/bcmwl5.inf / bcmwl5.sys 


The last entry refers to the BCM4303 but the others have the same pciid
I downloaded the file  SP30379.exe from the HP site at the following URL:
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31559-1&lc=en&cc=us&dlc=en&product=437690&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31559-1&lc=en&cc=us&dlc=en&product=437690&os=228&lang=en)
From the terminal I used the cabextract command on this file and extracted the bcmwl5.inf and bcmwl5.sys files.You may need to install cabextract here.
I believe these would work for your situation instead of the ones you are trying to use.

---

### Post by kipling100 on 2007-04-03
That worked for me!
Thanks for your help, I really appreciate it.

---

### Post by dansm15 on 2007-04-14
I figured out how to clean out the current settings, such that I now have this following listing upon doing an iwconfig:

dansm15@dandell:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

dansm15@dandell:~$

I downloaded SP30379.exe as suggested. I created a new directory at home/dansm15/extracted/SP30379.exe

I tried using the cabextract command but cannot seem to get it to work. This is the message I get:

dansm15@dandell:~$ cabextract.home/dansm15/extracted/SP0379.exe
bash: cabextract.home/dansm15/extracted/SP0379.exe: No such file or directory

Not sure where to go from here

Thx

Dan

---

