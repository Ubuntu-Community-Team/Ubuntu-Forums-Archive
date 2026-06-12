---
title: "Wireless Networking Bricked - M6300 + Broadcom"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by lwsiv on 2008-10-23
I have an 64 bit Dell M6300. When I first installed 8.04 (Hardy), everything (networking) was flawless. Initially it installed the Broadcom B43 Driver, then later is asked to upgrade to the STA driver. Things ran fine for a couple of days, then the machine started locking up. To the point it bricked my machine one day and I had to use the install disk to run fsck and get the inodes back straight.

I got the machine back up and running and have a network if I am plugged in, but wireless seems to flake out. It will sometimes show the available wireless networks, sometimes not. I thought one day I got it back on the wireless network, but then it may not have because I had it plugged in as well. I have disabled the STA driver and gone back to the B43. Sometimes when I do so, the wireless networks come back, but then they go away.

I have read the forum entries about other similar systems and it looks like the lock up/bricking is related to the STA driver and the 0.6.6-0ubuntu5 network-manager software. I went back to the B43 and downgraded to the 0.6.6-0ubuntu1 network manager, but the wireless networks are not showing up and I can't manually connect to them.

Any ideas?

---

### Post by Ayuthia on 2008-10-23
I am guessing that the driver is locking up the system and the card is not bricked (no longer functioning).

Can you post the results of the following:
```
lspci -nn
lshw -C network
uname -r
```

A lot of changes have happened lately so it will help to see what chipset you have, what driver your system is trying to use, and which kernel you are running.

---

### Post by lwsiv on 2008-10-23
lwsiv@mindninja:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:061c] (rev a2)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)


lwsiv@mindninja:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:21:70:99:c1:5e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5756m-v3.09 ip=10.22.44.162 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:68:c4:66:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


lwsiv@mindninja:~$ uname -r
2.6.24-21-generic

---

### Post by Ayuthia on 2008-10-23
Can you check and see if the b43 module is loaded with no other wireless module:
```
lsmod|grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
```
If wl shows up, then it is interfering with the b43 module.

The other thing to try is to go back to 2.6.24-19.  It  might be possible that one of the patches for the b43 module has changed the way your card is operating.

---

### Post by lwsiv on 2008-10-23
wl didn't show up... I guess I am reluctant to go back, because it was working fine on this version of the kernal for days. It was only after I bricked the machine and screwed up the filesys (had to run fsck to fix), due to the lock up that I had this problem. Is there any way to unload and reload everything wireless, or something similar?

---

### Post by Ayuthia on 2008-10-23
> **lwsiv said:**
> wl didn't show up... I guess I am reluctant to go back, because it was working fine on this version of the kernal for days. It was only after I bricked the machine and screwed up the filesys (had to run fsck to fix), due to the lock up that I had this problem. Is there any way to unload and reload everything wireless, or something similar?

You can try and reinstall the firmware by using b43-fwcutter again.  There should be a script in /usr/share/b43-fwcutter (or bcm43xx-fwcutter) that is called install_bcm43xx-fwcutter.sh.  It should be just a matter of going into /usr/share/b43-fwcutter and running:
```
sudo ./install*bcm43xx*.sh
```
If you see the actual file I am talking about, use that filename instead of the one I provided.  If you need more help with it, please post the result of 
```
ls /usr/share/b*
```

---

### Post by lwsiv on 2008-10-23
How do I restart it all, or do I have to reboot? I am not sure if it installed it, the paths look weird:

lwsiv@mindninja:/usr/share/b43-fwcutter$ sudo ./install*bcm43xx*.sh
[sudo] password for lwsiv: 
--13:22:10--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      106.96K/s    ETA 00:00

13:22:18 (85.49 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--13:22:18--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072       86.80K/s    ETA 00:00

13:22:28 (86.29 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

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

---

### Post by Ayuthia on 2008-10-23
> **lwsiv said:**
> How do I restart it all, or do I have to reboot? I am not sure if it installed it, the paths look weird:

lwsiv@mindninja:/usr/share/b43-fwcutter$ sudo ./install*bcm43xx*.sh
[sudo] password for lwsiv: 
--13:22:10--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      106.96K/s    ETA 00:00

13:22:18 (85.49 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--13:22:18--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072       86.80K/s    ETA 00:00

13:22:28 (86.29 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

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
It actually looks fine.  It cut out the firmware portions that it needed and placed it into the proper directories in /lib/firmware. 

You don't really need to reboot.  It should just be a matter of restarting the module:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
You probably don't really need to remove all of those modules, but I just like to be sure that it is all removed.

---

### Post by lwsiv on 2008-10-23
It looks like wireless is still bricked... Man, and I was so bragging about how easy Ubuntu had gone on this machine. Hell I am still trying to get XP installed right...

I am thinking I just need to go back to the previous version of Ubuntu (before hardy). It has been running very stably on my other dell laptop!

lwsiv@mindninja:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

tun0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by Ayuthia on 2008-10-23
You could also go back to 2.6.24-19 or live life on the bleeding edge and try out Intrepid's release candidate.  It is using the 2.6.27 kernel which seems to be better, but I am not for sure about how well it works in Ubuntu yet.  I plan to try to install it if I can get DSL activated next week.  The b43 module works pretty well in Arch using the 2.6.27 kernel though.  I have a 4311 rev 01 card so things might be different for you.

---

### Post by lwsiv on 2008-10-24
I went back to the previous kernal (19), no luck. Seems like whatever happened when fsck ran (which looked to be mainly changing group issues) it hosed up either the firmware or the network-manager. Any way of reinstalling ubuntu, and keeping my apps and my data? Or any other options you know of to fix this?

---

### Post by Ayuthia on 2008-10-24
> **lwsiv said:**
> I went back to the previous kernal (19), no luck. Seems like whatever happened when fsck ran (which looked to be mainly changing group issues) it hosed up either the firmware or the network-manager. Any way of reinstalling ubuntu, and keeping my apps and my data? Or any other options you know of to fix this?

I usually just backup my data and then reinstall my apps.  Here is a link that discusses how to track all the repository installed apps:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

Hope that helps.

---

