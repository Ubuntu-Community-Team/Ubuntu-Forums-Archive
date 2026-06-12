---
title: "newbie wireless help"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by cb81490 on 2008-10-03
Alright well i am sort of a newbie to linux i have some experience but im not a pro quite yet. I am having a problem getting my wireless card to work on my compaq m2000, the wireless card is broadcom bcm4306 i am new to linux but not new to forums site i have throughly searched and attempted all ways i have found. Installing the firmware through a terminal did work but the wireless card still does not work and is not recgonized by the device manager. The other way i tryed was using ndiswrapper which didnt work because the windows drivers for the bcm4306 are not like others and didnt contain the right files in it. what i mean is there was only the sys file not the other file not sure what is was called started with a "i". i was hoping someone could either show me a different way or help me get the correct wireless drivers so i can use ndiswrapper. also when try to connect to a wireless network i can not enter anything in the bssids or security i am guesing that is because the computer is yet to get the proper drivers installed for the wireless card. Also i am using ubuntu. thanks any help would be appriciated.

---

### Post by Idefix82 on 2008-10-03
Have you tried this tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

It should work but you have to read it very carefully. Please report back here and if you can't get it to work, people will sort you out.

---

### Post by Ayuthia on 2008-10-03
> **cb81490 said:**
> Alright well i am sort of a newbie to linux i have some experience but im not a pro quite yet. I am having a problem getting my wireless card to work on my compaq m2000, the wireless card is broadcom bcm4306 i am new to linux but not new to forums site i have throughly searched and attempted all ways i have found. Installing the firmware through a terminal did work but the wireless card still does not work and is not recgonized by the device manager. The other way i tryed was using ndiswrapper which didnt work because the windows drivers for the bcm4306 are not like others and didnt contain the right files in it. what i mean is there was only the sys file not the other file not sure what is was called started with a "i". i was hoping someone could either show me a different way or help me get the correct wireless drivers so i can use ndiswrapper. also when try to connect to a wireless network i can not enter anything in the bssids or security i am guesing that is because the computer is yet to get the proper drivers installed for the wireless card. Also i am using ubuntu. thanks any help would be appriciated.

There are a couple of options.  You can try going the bcm43xx route.  Some people have had better luck with them.  

The other option is trying this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

As for the .sys and the .inf files, you do need both.  The bcmwl5.inf file is needed to install the driver.  The bcmwl5.sys (32-bit) or bcmwl564.sys (64-bit) is what ndiswrapper uses to make it work.  However, the no-fluff site does have some options for you, but you will need to find out if you have a rev 02 or rev 03 version of the 4306 card (lspci -nn or lshw -C network).

---

### Post by cb81490 on 2008-10-03
i have completed step 3 in the wifidocs installation document but the wireless still does not work and the drivers say it is still not installed in device manager the drivers were without a doubt sucessfully installed, i am guessing i am going to have to figure out the Hardy Heron fix but i am confused i know i need to install this because it does say module instead of ndiswrapper when i run the lshw -c command....don't quote me on the command but thank you for the quick reply's so far i feel i almost got it so i am stil trying to figure out hard heron if anyone could help with that it would be appricated it already errored out of me when i tried the sudo rmmod ssb command but it says it could have 3 errors that are ok>? i am confused but still trying!

---

### Post by cb81490 on 2008-10-03
also i have figured out the i have the rev 03 version of my broadcom bcm 4306 card

---

### Post by Idefix82 on 2008-10-03
Could you post the output from 
```
lshw -C network
```
here?

---

### Post by cb81490 on 2008-10-03
connor@connor-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:89:f3:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.43 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
connor@connor-laptop:~$

---

### Post by Idefix82 on 2008-10-03
So what is the output from
```
sudo modprobe ndiswrapper
```

---

### Post by Ayuthia on 2008-10-03
You don't have to worry about the Hardy fix.  You don't need it because you don't have a Broadcom wired card.

Please try the following:
```
sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
sudo dmesg|grep ndiswrapper
```
The first command will remove any possible conflicting wireless driver, then it will try to load ndiswrapper.  Next it will try to scan for wireless sites.  We are also going to check dmesg to see if any error messages show up for ndiswrapper.

---

### Post by cb81490 on 2008-10-03
connor@connor-laptop:~$ sudo modprobe -r b43 ssb bcm4306 wl ndiswrapper
[sudo] password for connor: 
FATAL: Module bcm4306 not found.



connor@connor-laptop:~$ sudo modprobe ndiswrapper
connor@connor-laptop:~$

---

### Post by cb81490 on 2008-10-03
i thought i was suppose to put 4306 when it said 43xx but i realized i didnt and the command worked. but then i tryed the next command and it frooze the computer up completely and forced me to reboot

---

### Post by cb81490 on 2008-10-03
connor@connor-laptop:~$ sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
[sudo] password for connor: 
connor@connor-laptop:~$ sudo modprobe ndiswrapper
connor@connor-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

connor@connor-laptop:~$ sudo dmesg|grep ndiswrappe
[   70.487050] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   70.966513] usbcore: registered new interface driver ndiswrapper
[  317.219442] usbcore: deregistering interface driver ndiswrapper
[  335.496679] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  335.577938] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[  335.583134] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: f8ec7779
[  335.583145] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[  335.583236] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  335.583245] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  335.583273] ndiswrapper (mp_halt:259): device f2934480 is not initialized - not halting
[  335.583277] ndiswrapper: device eth%d removed
[  335.583333] ndiswrapper: probe of 0000:02:06.0 failed with error -22
[  335.583411] usbcore: registered new interface driver ndiswrapper
connor@connor-laptop:~$

---

### Post by Idefix82 on 2008-10-05
What is the output of
```
lspci
```

---

### Post by cb81490 on 2008-10-05
connor@connor-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
connor@connor-laptop:~$

---

### Post by Geoffrm on 2008-10-11
:KS> **Idefix82 said:**
> Have you tried this tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

It should work but you have to read it very carefully. Please report back here and if you can't get it to work, people will sort you out.
Hi, I am a newbie to Linux (ubuntu 8.04) but not to the world of MS Dos Dr Dos and of course MS XP etc howerver I wanted a new challenge at the age of 63. I was trying all the links to get my Dell lattitude D600 Broadcom BCM4306 to work. After following all the threads using GUI or terminal I was getting the message to insert the Ubuntu CD for ndiswrapper ??  on mounting the CD the file could not be found. I Then found that in System / administration/Software Sources the Installable from CD-Rom/DVD was set after unchecking this all worked fine and I now have the BCM4306 working with a Linksys 54g  wireless access piont. I hope this is of help to any newbies like myself. Thanks to Unbutu super friendly forums.

---

### Post by cb81490 on 2008-10-14
that did not effect anything thanks for trying though i cannot figure this out i have read all threads on it my only way if someone can help me on here.

---

### Post by Ayuthia on 2008-10-14
> **cb81490 said:**
> that did not effect anything thanks for trying though i cannot figure this out i have read all threads on it my only way if someone can help me on here.

It looks like ndiswrapper does not like the driver.  What computer are you using (make/model)?  

Another option is to try using the b43 drivers.  I think that they will work with your computer.  If you want to use this, please install b43-fwcutter.  Once that is done, please go into the Terminal and do the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by cb81490 on 2008-10-16
ok i will try that my computer is a compaq m2000

---

### Post by cb81490 on 2008-10-16
connor@connor-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
[sudo] password for connor: 
--15:04:28--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      228.13K/s             

15:04:31 (227.50 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--15:04:31--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      276.52K/s    ETA 00:00

15:04:35 (262.11 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
connor@connor-laptop:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
connor@connor-laptop:~$ sudo modprobe b43
connor@connor-laptop:~$ sudo ifconfig wlan0 up
connor@connor-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:E2:32:21
                    ESSID:"05Z401602929"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=73/100  Signal level=-59 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001179d0047b4
          Cell 02 - Address: 00:E0:98:F0:B1:BC
                    ESSID:"05B406908336"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a622cf8122
          Cell 03 - Address: 00:14:6C:7E:E0:60
                    ESSID:"SOTS"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000004c64a72183

connor@connor-laptop:~$ 



ok that worked great it showed my network but i still cannot just search for a network or type in the ssids for the wireless networks

---

### Post by cb81490 on 2008-10-16
connor@connor-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
[sudo] password for connor: 
--15:04:28--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      228.13K/s             

15:04:31 (227.50 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--15:04:31--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      276.52K/s    ETA 00:00

15:04:35 (262.11 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
connor@connor-laptop:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
connor@connor-laptop:~$ sudo modprobe b43
connor@connor-laptop:~$ sudo ifconfig wlan0 up
connor@connor-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:E2:32:21
                    ESSID:"05Z401602929"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=73/100  Signal level=-59 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001179d0047b4
          Cell 02 - Address: 00:E0:98:F0:B1:BC
                    ESSID:"05B406908336"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a622cf8122
          Cell 03 - Address: 00:14:6C:7E:E0:60
                    ESSID:"SOTS"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000004c64a72183

connor@connor-laptop:~$ 



ok that worked great it showed my network but i still cannot just search for a network or type in the ssids for the wireless networks

---

### Post by Ayuthia on 2008-10-16
> **cb81490 said:**
> connor@connor-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
[sudo] password for connor: 
--15:04:28--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      228.13K/s             

15:04:31 (227.50 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--15:04:31--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      276.52K/s    ETA 00:00

15:04:35 (262.11 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
connor@connor-laptop:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
connor@connor-laptop:~$ sudo modprobe b43
connor@connor-laptop:~$ sudo ifconfig wlan0 up
connor@connor-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:E2:32:21
                    ESSID:"05Z401602929"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=73/100  Signal level=-59 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001179d0047b4
          Cell 02 - Address: 00:E0:98:F0:B1:BC
                    ESSID:"05B406908336"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a622cf8122
          Cell 03 - Address: 00:14:6C:7E:E0:60
                    ESSID:"SOTS"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-67 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000004c64a72183

connor@connor-laptop:~$ 



ok that worked great it showed my network but i still cannot just search for a network or type in the ssids for the wireless networks

You might want to check and see if roaming is enabled.

You can also try turning off encryption to see if you can connect.  If it does not work through the GUI section, please try the following in the Terminal (with encryption turned off):
```
sudo iwconfig wlan0 essid 05Z401602929
sudo dhclient wlan0
```

---

### Post by cb81490 on 2008-10-17
wow after a whole two weeks of trying i finally got it to work! thank you for the help couldn't have done it without you guys. Only issue i have now is that the settings or maybe driver doesn't save the settings when i restart how do i make this save so it always works?

---

### Post by Ayuthia on 2008-10-17
> **cb81490 said:**
> wow after a whole two weeks of trying i finally got it to work! thank you for the help couldn't have done it without you guys. Only issue i have now is that the settings or maybe driver doesn't save the settings when i restart how do i make this save so it always works?

You will need to update your /etc/modprobe.d/blacklist and /etc/modules.  It might be easier if you post the results of:
```
cat /etc/modprobe.d/blacklist
cat /etc/modules
```
It will list out what is in the two files and we can determine what we need to add/remove.

---

### Post by cb81490 on 2008-10-17
connor@connor-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist wl
blacklist bcm43xx
blacklist wl
connor@connor-laptop:~$ cat /etc/modules

---

