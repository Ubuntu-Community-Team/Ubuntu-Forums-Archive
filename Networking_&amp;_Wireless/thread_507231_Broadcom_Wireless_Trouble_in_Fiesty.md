---
title: "Broadcom Wireless Trouble in Fiesty"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Rando303 on 2007-07-22
I am new to Ubuntu.  This is my first time running Linux of any flavor on a laptop.  After Best Buy Geek Squad completely destroyed my preloaded Windows and lost my restore disks, I refuse to order a new set for $30 and so, here I am.  The laptop is a Gateway laptop a few years old.  The internal wireless card is a Broadcom BCM4306.  The internal sound card is an Intel 82801 DB.

    Starting from a fresh Feisty install, WiFi is no-go, sound is no-go.  After following several guides on this forum I was able to enable WiFi with ndiswrapper.  After this I fixed the sound issue using the Comprehensive sound Guide.  I restarted several times and everything was still working just fine.  Then I installed the 80 some available updates and restarted.  After this the sound is still functional but wireless internet is lacking all function.  The card is still detected and the driver still installed, but it does not detect any wireless networks in range (when I verified the existence with desktop sitting right by the laptop) and can't connect manually.  I followed the same exact guides in the same order as I did to originally fix the problem, and still no functionality.   After this I went on to follow any and all guides found when searching for "Broadcom BCM4306 Fiesty" on the forums.  Nothing up to this point has worked.  Any help would be greatly appreciated and any further info that would be helpful can be provided.

---

### Post by gangolli on 2007-07-24
Can you post the output of

> 
lshw -C network


and 

> 
lsmod | grep bcm


---

### Post by Rando303 on 2007-07-24
> lshw -C network

produced the following output:

  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:22:33:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.131 latency=64 multicast=yes
       resources: iomemory:e00fc000-e00fdfff irq:18
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:db:70:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,03/23/2006, 4.40.1 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e00f6000-e00f7fff irq:19


> lsmod | grep bcm

produced no output

---

### Post by gangolli on 2007-07-25
This looks fine so far.

Also some basic things to check while we're at it:
- If your laptop has a switch to turn off the radio, can you make sure it is not turned off.  
- Check that the wireless enabled in the BIOS if there is a setting applicable to that.

And more diagnostics to look for anything abnormal.

> 
ndiswrapper -l


> 
dmesg | grep ndis


> 
dmesg | grep wlan


> 
iwconfig


> 
iwlist wlan0 scan


---

### Post by Rando303 on 2007-07-25
Wow! Thank you so much!  I won't bother posting the diagnostic results because all was well.  I feel dumb for not checking, but there IS a wireless power setting in the BIOS.  It was still set to "Restore" which works for the preloaded Windows XP, but changing the setting to "On" fixed it.  Thanks for your help!

---

