---
title: "Can't compile the ralink rt61 wireless driver... :("
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Starlight on 2006-10-28
Hi! I tried to install the ralink rt61 driver according to the instructions here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11) but I couldn't, even though I did everything just like it was in the readme file...

When I tried to do "make all", it said that I don't have the directory /lib/modules/2.6.17-10-386/build, so I created it. Then when I tried to compile it, it said something like "no rule to create target", and I have no idea what this error even means... can someone tell me how to compile it? I tried to compile it as root, and I got the same error.

---

### Post by kanchata on 2006-10-28
> **Starlight said:**
> Hi! I tried to install the ralink rt61 driver according to the instructions here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11) but I couldn't, even though I did everything just like it was in the readme file...

When I tried to do "make all", it said that I don't have the directory /lib/modules/2.6.17-10-386/build, so I created it. Then when I tried to compile it, it said something like "no rule to create target", and I have no idea what this error even means... can someone tell me how to compile it? I tried to compile it as root, and I got the same error.

Have your kernel sources && headers properly installed

---

### Post by kanchata on 2006-10-28
> **kanchata said:**
> Have your kernel sources && headers properly installed

rt61pci can't scan or associate
Re: rt61pci can't scan or associate from Karsten Dello at 2006-10-27 15:12:38 UTC

Had the same problem. The card ran fine using rt61-module in dapper, but I couldn't get it to work using the rt61pci-module in edgy. Have spent hours but could not get it to work.

But the card works flamelessly in edgy using the ratech drivers (rt61).
Here is what I did:

1) i got the drivers from [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)

2) followed the readme to compile the kernel-module.
the rt61-module compiles fine, as [COLOR="Red"]usual linux-headers were required.[/COLOR]
copied the firmware and the modified configuration file (set up ssid,wpa etc.) to /etc/Wireless/RT61STA/
Afterwards copied rt61.ko somewhere below /lib/modules/<kernel-version/
and run depmod

3) blacklisted the - broken? - ubuntu kernel module in /etc/modprobe.d/blacklist:
blacklist rt61pci

4) added the ratech-module in /etc/modules
and put an alias in /etc/modprobe.d/aliases:
alias ra0 rt61

5) added the following lines to /etc/network/interfaces:

iface ra0 inet static
address 192.168.7.228
netmask 255.255.255.0
gateway 192.168.7.1
auto ra0

Works perfectly for me.

---

### Post by Starlight on 2006-10-29
I remember I installed the kernel headers, just like the instructions said... but I didn't install kernel sources, unless they were already installed... I'll try to get them.

---

### Post by Starlight on 2006-10-29
It still doesn't work :( When I compile it, I get a lot of weird warnings...

```
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_main.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_main.c:39:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:39:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿSTAMlmePeriodicExecÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:734: warning: unused variable ÔÇÿRxSignalÔÇÖ
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿAsicSwitchChannelÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:3671: warning: comparison is always false due to limited range of data type
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿAsicSetRxAntÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5397: warning: ÔÇÿR77ÔÇÖ may be used uninitialized in this function
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5421: warning: ÔÇÿR77ÔÇÖ may be used uninitialized in this function
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5446: warning: ÔÇÿR77ÔÇÖ may be used uninitialized in this function
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿRadarDetectionStopÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5781: warning: ÔÇÿR66ÔÇÖ may be used uninitialized in this function
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿAsicAdjustTxPowerÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:4268: warning: ÔÇÿBbpR1ÔÇÖ may be used uninitialized in this function
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ÔÇÿAsicSwitchChannelÔÇÖ:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:3588: warning: ÔÇÿBbpRegÔÇÖ may be used uninitialized in this function
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/connect.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/connect.c:37:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/sync.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/sync.c:38:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/assoc.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/assoc.c:37:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/auth.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/auth.c:37:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/auth_rsp.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/auth_rsp.c:27:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_data.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_data.c:39:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_init.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_init.c:40:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/sanity.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/sanity.c:38:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_wep.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_wep.c:38:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.c:40:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/eeprom.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/eeprom.c:37:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_tkip.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_tkip.c:38:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/wpa.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/wpa.c:39:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/md5.o
In file included from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/md5.c:20:
/home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  LD [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.o
  Building modules, stage 2.
  MODPOST
  CC      /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.mod.o
  LD [M]  /home/piotrek/source/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic' 
```

And the module just doesn't work... I did everything as the instructions said, and there was even no ra0. When I tried to do "sudo modprobe rt61", I got this:

```
FATAL: Error inserting rt61 (/lib/modules/2.6.17-10-386/rt61.ko): Invalid module format
```

---

### Post by wieman01 on 2006-10-29
Have you installed the headers correctly? See screenshot... You version will differ, but I have 2 packages installed.

---

### Post by Starlight on 2006-10-29
I didn't install them from synaptic, because I don't have internet connection on Linux... so I downloaded the debs on Windows. I'll try to check in Ubuntu now, and then go back to Windows so that I can post it here...

---

### Post by wieman01 on 2006-10-29
Mmm... It seems to me that you have installed the wrong headers... You should install them from the Ubuntu CD. All package you may possibly need are on there. No need to download them at all.

---

### Post by wieman01 on 2006-10-29
You need to install the "build-essential" which you have not. Hence this error message: [COLOR="Red"]"Can't find kernel build files in /lib/modules/2.6.15-27-386/build;"[/COLOR]

> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-source-`uname -r`
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`
Try to run these from a terminal windows & recompile the driver.

---

### Post by Starlight on 2006-10-29
hmm... the problem is that I don't have the CD-ROM... I upgraded my Ubuntu from an ISO file of the alternate install CD, and after the upgrade I deleted it... I need to download the standard install CD and burn it. In the meantime, I've noticed that I forgot to install the linux headers 386 package, so I'll do it, and maybe it will work.

---

### Post by wieman01 on 2006-10-29
Alright... Download the ISO, burn it, install the headers & the remaining packages. Sounds like a good solution. :-) Drop us a line if you still have problems installing the driver. But you'll be fine I guess.

---

### Post by Starlight on 2006-10-29
It works! :D I'm posting this from my Ubuntu now... :)

It didn't work before because I had installed the "generic" headers instead of "386".... this time it also gave warnings while compiling, but the driver works well! :) Thanks for your help!

---

### Post by kanchata on 2006-10-29
Hello, I´re recent (not for linux) with Xubuntu 6.10 (Edgy Eft) installed I´we downloaded the alternete iso i386 and installed all kernel headers & linux image with synaptic from cd source and rt2x00 (testing)drivers of rt2x00-serialmonkey are installed, make the config for proper driver & others tip´s, make && make install, insmod modules.ko (rt61pci,rt2500,rt2400, usb,,,,etc.) with same step from README, and the modules are properly installed without error, anothers question is a wifi connection d´nt work for anothers problems.

---

### Post by wieman01 on 2006-10-29
> **kanchata said:**
> Hello, I´re recent (not for linux) with Xubuntu 6.10 (Edgy Eft) installed I´we downloaded the alternete iso i386 and installed all kernel headers & linux image with synaptic from cd source and rt2x00 (testing)drivers of rt2x00-serialmonkey are installed, make the config for proper driver & others tip´s, make && make install, insmod modules.ko (rt61pci,rt2500,rt2400, usb,,,,etc.) with same step from README, and the modules are properly installed without error, anothers question is a wifi connection d´nt work for anothers problems.
Post the contents of this file:
> sudo gedit /etc/network/interfaces
Then also do a scan & post the results:
> iwlist scan

---

