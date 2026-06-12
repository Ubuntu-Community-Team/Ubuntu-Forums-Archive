---
title: "Wireless Network trouble in Ubuntu 8.04"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by cheeZ on 2008-05-08
Hi, I need help on getting Ubuntu 8.04 (Hardy Heron) to connect to my wireless network. I have just installed Ubuntu yesterday, and I love it. But it's really useless to me if I can't connect to the internet. I googled everything I could and even searched extensively in these forums, but** nothing works.** Any help would be **greatly** appreciated.

[CENTER]**_Extra details_**[/CENTER]

Network Adapters: **Broadcom 440x 10/100 Integrated Controller** and **Broadcom 802.11g Network Adapter**

Computer make and model: **Acer Aspire 3690**

If there are any more details you need please ask.


P.S. I am running a dual-boot laptop with both Vista and Ubuntu (Vista installed first).

---

### Post by Ayuthia on 2008-05-08
> **cheeZ said:**
> Hi, I need help on getting Ubuntu 8.04 (Hardy Heron) to connect to my wireless network. I have just installed Ubuntu yesterday, and I love it. But it's really useless to me if I can't connect to the internet. I googled everything I could and even searched extensively in these forums, but** nothing works.** Any help would be **greatly** appreciated.

[CENTER]**_Extra details_**[/CENTER]

Network Adapters: **Broadcom 440x 10/100 Integrated Controller** and **Broadcom 802.11g Network Adapter**

Computer make and model: **Acer Aspire 3690**

If there are any more details you need please ask.


P.S. I am running a dual-boot laptop with both Vista and Ubuntu (Vista installed first).
Can you also include the results from:
```
lspci -nn
```
It will provide all your PCI information including their id numbers.  It will help determine which method you can use.

---

### Post by cheeZ on 2008-05-09
Sure thing. Here's what came up after typing "lspci -nn" into Terminal:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)

---

### Post by Ayuthia on 2008-05-09
> **cheeZ said:**
> Sure thing. Here's what came up after typing "lspci -nn" into Terminal:

05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

This one is your wireless card.  You have two options:

Use the native b43 driver:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Or you can try NDISwrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

I have the same network card and both b43 and NDISwrapper work about the same on it.  I would suggest that you try the b43 install first because it is easier, has less steps, and is easier to switch to NDISwrapper if you do not like it.  NDISwrapper has more steps, is harder to configure, and more difficult to switch back to b43.  However, those who tend to use it seem to be more happy with it mainly because they think that it is faster and more reliable.

---

### Post by cheeZ on 2008-05-09
Thank you for going to the trouble to help me out. However nothing seems to be working. First I clicked on your first link to try out the b43 driver. I followed every instruction on that page, but no luck. EVERY TIME I entered something into the terminal, some kind of stupid error occured and it wasn't able to process my command. Here is everything that happened in the terminal from begginning to end:

colbz@colbuntu:~$ cd
colbz@colbuntu:~$ sudo dpkg -i b43-fwcutter_011-1_i386.deb
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ cd
colbz@colbuntu:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ tar xfvj broadcom-wl-4.80.53.0.tar.bz2
tar: broadcom-wl-4.80.53.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
colbz@colbuntu:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ sudo ifconfig wlan0 up
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ 

I checked and could not find any errors whatsoever in my typing, yet it wasn't able to do anything, much less connect to the internet.

And the second one, the NDISwrapper link, I don't even understand what to do. I figured out that step 2a is the step that will most likely work, but I don't know what to do! The instructions step 2a gave me is this:

```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe

```

Okay, first of all, how am I supposed to install a package if I'm NOT CONNECTED TO THE INTERNET!?!? I could maybe use Vista to download them onto my USB flash drive, so I can do the neccesary steps on Ubuntu, which is what I did for your instructions on "b43-fwcutter." But how am I supposed to even RUN a program that's in .exe format? I thought Linux wasn't able to run those types of files! Am I wrong on that?

Anyway, I appreciate you trying to help, and any future help from you would be awesome. Hopefully I'll get this wireless working before I go crazy and get thrown into a mental hospital...

---

### Post by Ayuthia on 2008-05-09
> **cheeZ said:**
> Thank you for going to the trouble to help me out. However nothing seems to be working. First I clicked on your first link to try out the b43 driver. I followed every instruction on that page, but no luck. EVERY TIME I entered something into the terminal, some kind of stupid error occured and it wasn't able to process my command. Here is everything that happened in the terminal from begginning to end:

colbz@colbuntu:~$ cd
colbz@colbuntu:~$ sudo dpkg -i b43-fwcutter_011-1_i386.deb
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ cd
colbz@colbuntu:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ tar xfvj broadcom-wl-4.80.53.0.tar.bz2
tar: broadcom-wl-4.80.53.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
colbz@colbuntu:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ sudo ifconfig wlan0 up
sudo: unable to resolve host colbuntu
colbz@colbuntu:~$ 

I checked and could not find any errors whatsoever in my typing, yet it wasn't able to do anything, much less connect to the internet.

And the second one, the NDISwrapper link, I don't even understand what to do. I figured out that step 2a is the step that will most likely work, but I don't know what to do! The instructions step 2a gave me is this:

```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe

```

Okay, first of all, how am I supposed to install a package if I'm NOT CONNECTED TO THE INTERNET!?!? I could maybe use Vista to download them onto my USB flash drive, so I can do the neccesary steps on Ubuntu, which is what I did for your instructions on "b43-fwcutter." But how am I supposed to even RUN a program that's in .exe format? I thought Linux wasn't able to run those types of files! Am I wrong on that?

Anyway, I appreciate you trying to help, and any future help from you would be awesome. Hopefully I'll get this wireless working before I go crazy and get thrown into a mental hospital...

Ok.  Looks like you have a problem with using sudo.  We need to figure out how to fix this so that you can move forward.

---

### Post by Ayuthia on 2008-05-09
You might want to check this out:
[http://ubuntuforums.org/showthread.php?t=613521&page=2](http://ubuntuforums.org/showthread.php?t=613521&page=2)

It deals with your issue with sudo.  Hope that helps.

---

### Post by vigyani on 2008-05-09
Hi

Try booting using Kernel 2.6.22-14 instead of 2.6.22-16. For me wireless works fine in 2.6.22-14. It seems 2.6.22-16 has some problem with Broadcom drivers.

Please see:
[http://ubuntuforums.org/showpost.php?p=4919626&postcount=81]("http://ubuntuforums.org/showpost.php?p=4919626&postcount=81")

regards
Vig

---

### Post by Ayuthia on 2008-05-09
> **vigyani said:**
> Hi

Try booting using Kernel 2.6.22-14 instead of 2.6.22-16. For me wireless works fine in 2.6.22-14. It seems 2.6.22-16 has some problem with Broadcom drivers.

Please see:
[http://ubuntuforums.org/showpost.php?p=4919626&postcount=81]("http://ubuntuforums.org/showpost.php?p=4919626&postcount=81")

regards
Vig

vigyani-
That post is related to an NDISwrapper upgrade instead of a b43 upgrade.

---

### Post by cheeZ on 2008-05-09
Okay, I decided that I must've done something that screwed up the sudo or something, so I thought the best idea would be to uninstall Ubuntu and then re-install it. I first installed Ubuntu through Wubi, since I was unable to shrink my partition OR burn a live CD, so I am doing the same thing now. Wubi is still running, and there is about 1 hour 23 minutes left... And I started it an hour ago! And the KB/s is getting lower and lower by the minute. Is it supposed to be this slow? My normal download speed is at LEAST 350 KB/s, so I don't know why this download is taking so long. Oh well, I can't complain, Ubuntu IS an awesome OS. As soon as it's installed I'll go through all those steps again to see if I get a different result, and report back here if I run into any problems. You've been a great help, thank you! :)

---

### Post by cheeZ on 2008-05-09
Alright, I re-installed Ubuntu successfully, and the first thing I did when I got on was try those steps again in terminal. Here is everything that happened in the Terminal:

colbra@colbra-laptop:~$ cd
colbra@colbra-laptop:~$ sudo dpkg -i b43-fwcutter_011-1_amd64.deb
(Reading database ... 94962 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:011-1 (using b43-fwcutter_011-1_amd64.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:011-1) ...

colbra@colbra-laptop:~$ cd
colbra@colbra-laptop:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
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
colbra@colbra-laptop:~$ tar xfvj broadcom-wl-4.80.53.0.tar.bz2
tar: broadcom-wl-4.80.53.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
colbra@colbra-laptop:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
Cannot open input file broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
colbra@colbra-laptop:~$ sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
chmod: cannot access `/lib/firmware/b43': No such file or directory
colbra@colbra-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

I then tried to connect to my wireless network, no luck. Restarted my computer, and tried again... no luck. Did I do something wrong? I download all the neccessary files onto a flash drive, and copied them to the Home Directory in Ubuntu. But still nothing seems to work, there's always some kind of error. One thing I noticed though, was that when you said to give this command:

```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
```

The download link you provided linked to a file in ".tar" format, not ".bz2." Could that be the problem?

**[SIZE="5"]*UPDATE!!!!*[/SIZE]**

I found a spare ethernet cable, and wanted to see what would happen if I connected my computer to my modem, and to my surprise, I was connected to the internet!!! :guitar: I didn't know that was possible! Anyway, I still don't have wireless working, so if there are any better steps to take that require an internet connection, I am now able to follow those steps. I'm even writing this from Ubuntu right now, this is so cool!!! \\:D/

---

### Post by Ayuthia on 2008-05-09
> **cheeZ said:**
> 
colbra@colbra-laptop:~$ tar xfvj broadcom-wl-4.80.53.0.tar.bz2
tar: broadcom-wl-4.80.53.0.tar.bz2: Cannot open: No such file or directory


This is saying that the file is not in your home directory.  Is that where you put the file?  You need to be in the directory where that file is located and then it should extract just fine and you should be able to continue from that step.

If it does not extract, please show the result of:
```
ls -l broadcom-wl-4.80.53.0*
```

---

### Post by cheeZ on 2008-05-10
After searching around I came across [this thread.]("http://ubuntuforums.org/showthread.php?t=766560") Since I was able to connect to the internet from my ethernet cable, I was able to successfully download everything I needed through the terminal following each step. And I can't believe it, it worked PERFECTLY. After restarting my computer, it actually saw my network and was able to connect to it perfectly. I'm sorry if I made you go to any trouble when there was already thread that had the answer I was looking for. Thank you though, I appreciate you taking the time to help point me in the right direction. You can't imagine how grateful I am to have wireless now, before I thought there was no hope at all! Thanks again, 

**[COLOR="DarkOrange"][FONT="Courier New"]cheeZ[/FONT][/COLOR]**

---

