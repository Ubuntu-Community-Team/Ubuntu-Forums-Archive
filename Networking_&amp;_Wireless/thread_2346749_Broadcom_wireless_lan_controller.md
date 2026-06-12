---
title: "Broadcom wireless lan controller"
date: 2016-12-18
forum: Networking &amp; Wireless
---

### Post by dougcumiskey123 on 2016-12-18
Although I have been using Ubuntu  for several years I still class myself as very much a novice.

I have installed Ubuntu 16.04 onto an old fujitsu/Siemens laptop and found I had no wifi so using another working Ubuntu computer I went looking for a cure.

using ...  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) I got....................

doug@doug-AMILO-A1650:~$ lspci -vvnn | grep -A 9 Network
02:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Gemtek Technology Co., Ltd BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [17f9:0006]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb 

My problem is that I am lost, I cant fined the correct file/driver to down load plus there seems to be no specific instructions for ubuntu 16.04 and and I don't want to try just in case I crash it and have to start again.

Can some kind sole help me out.

Doug.

---

### Post by howefield on 2016-12-18
Thread moved to the "*Networking & Wireless*" for a better fit.

---

### Post by jeremy31 on 2016-12-18
See if this post by Hadaka helps
[https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)

---

### Post by dougcumiskey123 on 2016-12-18
Thanks Jeremy I have hit a snag, it seems to be looking for the file that was purged on the first line IE bcmwl-kernel-source. Have I missed something? I still have no wifi.


doug@doug-AMILO-A1650:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
doug@doug-AMILO-A1650:~$ sudo rm /ect/modprobe.d/blacklist-bcm43.conf
rm: cannot remove '/ect/modprobe.d/blacklist-bcm43.conf': No such file or directory
doug@doug-AMILO-A1650:~$ sudo mkdir /lib/firmware/b43
doug@doug-AMILO-A1650:~$ sudo cp Desktop/b43/* /lib/firmware/b43
doug@doug-AMILO-A1650:~$ sudo modprobe b43
doug@doug-AMILO-A1650:~$

---

### Post by Hadaka on 2016-12-18
Hi, that is not a snag, its just saying the file you are attempting to purge is not there.
First do you have a working wired connection ? if *YES then do..
```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo modprobe b43

```
remove wired connection,any usb connections...boot and test wireless
*If NO you do NOT have a working wired connection ...did you find a way
to down load the the B43 ZIP file from the link that jeremy31 sent you ??
Please provide us with answers  to these questions.
Thanks

---

### Post by dougcumiskey123 on 2016-12-18
Sorry, I don't have a wired connection, I run on a MiFi unit that serves wifi to any and all computer here, I down loaded the the B43 zip file on a working computer then transferred the file to a USB memory stick and moved to onto the non working computer that way. 

Many thanks Doug

---

### Post by Hadaka on 2016-12-18
Hi Doug, no problem on the no wired connection, the method and link
that jeremy31 gave you is correct and has been used hundreds of times,
so let's see if we can figure out what is holding the wifi from loading.
please copy one line at a time and then post the output of,,
```
lspci -n | awk '/0280/{print$3}'
lsmod |awk '/802/'
rfkill list all | awk '/yes/'
```
are you attempting to load the driver in the "Try Ubuntu Mode" ???
or have you actually loaded Ubuntu ??
thanks.

---

### Post by dougcumiskey123 on 2016-12-19
OK Hadaka, first the printout on,,,,,,

lspci -n | awk '/0280/{print$3}'
lsmod |awk '/802/'
rfkill list all | awk '/yes/'


doug@doug-AMILO-A1650doug@doug-AMILO-A1650:~$ lspci -n | awk '/0280/{print$3}'
14e4:4318
doug@doug-AMILO-A1650:~$ lsmod |awk '/802/'
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
doug@doug-AMILO-A1650:~$ rfkill list all | awk '/yes/'
doug@doug-AMILO-A1650:~$ 

On the last line         rfkill list all | awk '/yes/'       There was no output.

On the installation mode, the doug@doug-AMILO-A1650 computer is a full installation of 16.04 on a clean HDD, no windows involved.

sorry for the delay in replying, only just climbed out of bed. Here I am on GMT time zone, what is your time zone

Doug.

---

### Post by Hadaka on 2016-12-19
Hi, thanks, it looks like your b43 driver is loaded. try this..
```
sudo modprobe -rf b43
sudo modprobe -v b43
dmesg | grep b43
```
please post the output of the dmesg result.
then do and post..
```
iwconfig
```
thanks.

---

### Post by dougcumiskey123 on 2016-12-19
Hadaka

I have got the wifi working, I don’t know how but I have found that the computer is running very, very slow, it was always a slow computer but now its so slow that any applications running gray-out and the keyboard buffers up. Strange as it was not that slow with windows XP and only 613MiB. I wonder if 16.04 is just too much for it.

I can only apologize for wasting your time and thank you for your help

Many thanks for your help, Doug

---

### Post by Hadaka on 2016-12-19
Great ! that is good news ! Let's see if we can figure out
the vintage of that old Fujitsu/Siemens. Please post the output of..
```
cat /sys/class/dmi/id/bios_date
```
Thanks.

---

### Post by dougcumiskey123 on 2016-12-19
Ok, its been a long day but I have sorted out the slowness on the computer, 

I reinstalled 16.04 but this time I left out the encryption program and the speed came up, that followed the instruction from "Hadaka" using the "B43" zip file and the wifi came up straight away with no problems at all.  Thank you very much Hadaka.

Doug

---

### Post by dougcumiskey123 on 2016-12-19
I just tried the line cat /sys/class/dmi/id/bios_date it worked on this computer "Lenovo T410" with 2013 but on the old fujitsu/siemens it came back with file not found, so I guess it pre dates the code, I bought it new about 10 or 12 years ago.

Doug.

---

### Post by Hadaka on 2016-12-19
Great ! looks like you have it all sorted out.
You are probably correct about the computer being so old it predates that code.
If you are satisfied with the wifi please take the time to mark your thread
solved by clicking Thread Tools and then Solved.
Thanks.

---

