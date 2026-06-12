---
title: "wireless works off live CD, but not from installed ubuntu"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by tyggna1 on 2007-08-18
I'm using Feisty, and I installed a wireless network card after installing my OS.  My new card is an aKia WN360G, and is listed as compatible with Ubuntu, but no "wireless" option appears in my network manager.  In my network settings, it saw two methods of wireless connection, wmaster1 and wlan0--both with the MAC address of my card.

I decided to try booting from the live CD, and lo-and-behold it works fine.  I believe that if I reinstalled my OS, then it would work, but I keep thinking "There's got to be an easier way!"  Is there anyway to simply reinstall my network manager?  Can I try a recovery option with a non-live CD?  Could someone at least offer a suggestion, or bounce an idea off me?

I'm at a loss.  Please help me.

---

### Post by tyggna1 on 2007-08-18
Since I can't find a satisfactory answer anywhere in the forum:  I'll just document what I try and what I use.  If it works: great!  I finally added something to the community.

First off:  I'm behind a router, and I'm wired most of the time.  I'm trying to get my wireless to work.  I use MAC filtering--but have all my cards on my access list.  I don't broadcast my SSID--but that hasn't been a problem on my Wife's computer.  She can connect fine.

I've uninstalled network-manager in the add/remove programs, and then restarted my computer.  Reinstalled the manager--and it wasn't able to recognize my wired network connection either.  After reboot, wired network worked, but the manager went right back to the way it was.  I'm going to try reinstalling both the manager and my updated kernel from my original feisty kernel.

---

### Post by tyggna1 on 2007-08-19
I attempted to reinstall all packages that included "networking" in their name by marking them for installation--but it didn't do anything.  I have time, so I'm gonna reinstall the kernel now, and let you know how that goes.  After the kernel, if it doesn't work, I'm gonna try finding any packages that I'm missing regarding network manager to see if that can enable wireless support.

---

### Post by bmartin on 2007-08-19
I think you have an intersil chipset. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=446010&highlight=intersil").

---

### Post by tyggna1 on 2007-08-19
iwlist scan reveals all the access points in my area in the terminal--but network manager doesn't do anything.    Sure enough, though, I have an Intersil chip set.  

Here's the result of 
sudo lshw -C network
> 
  *-network:0             
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: [COLOR="Red"]Intersil [/COLOR]Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: wmaster0
       version: 01
       serial: 00:0a:e9:0d:09:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=80 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0200000-c0201fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:d8:05:22
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=199.170.1.3 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:c0202000-c0202fff ioport:7000-703f irq:11


So what am I missing?  (still finishing the thread)

---

### Post by bmartin on 2007-08-19
Try using a different program to connect. [Here]("http://blakecmartin.googlepages.com/wicd.html") is a set of instructions I wrote to install WICD quickly (or [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html"), if you prefer). The built-in network manager is buggy.

To use WICD, type **wicd** or **wicd-tray** into a terminal (the wicd-tray program, which you'd've downloaded from my page, simply loads the tray icon program). To run wifi-radar, use **sudo wifi-radar**.

---

### Post by tyggna1 on 2007-08-19
wicd doesn't show any wireless networks.  I've tried all the drivers listed in the preferences, and tried both of the wireless interfaces showing in ubuntu (wmaster0 and wlan1).  I'll give wifi-radar a shot.

---

### Post by tyggna1 on 2007-08-19
wifi-radar tries to scan for wireless networks, but the terminal keeps posting

```

wmaster0  Interface doesn't support scanning : Operation not supported
```

---

### Post by bmartin on 2007-08-19
It might be the "competing WiFi drivers" problem as mentioned in the other thread. Try blacklisting the prism2_pci kernel module.

The three modules mentioned in that thread are orinoco_pci, hostap_pci, and prism2_pci. Try removing the last two and see if that makes a difference.

---

### Post by tyggna1 on 2007-08-19
of those three, lsmod only shows hostap.   there is a prism54pci on the complete list, though.  It may help to mention that it's Mini-PCI, though that shouldn't make any difference.

Anyway, I installed the orinoco drivers (orinoco_pci) and blacklisted prism54pci, prism54common, hostap_pci and hostap.  Still get the same message, wmaster0 can't scan.

---

### Post by bmartin on 2007-08-19
I'd try each of the modules, one at a time, using **modprobe -r** to remove a module and **modprobe** to insert one.

---

### Post by tyggna1 on 2007-08-19
<sigh> same message, same results.  I'm too tired, and have to be to work early in the morning.  I'll log on tomorrow and see if there's anything I can do.  Thanks for you help.

---

### Post by tyggna1 on 2007-08-20
Alright, I'm back.  I'm gonna try installing the prism2 drivers and using only those (as I have prism54).  If that doesn't work, I have another wireless card that is supposed to based off the Orinoco drivers.

---

### Post by tyggna1 on 2007-08-20
Well, it didn't work before all this--but my old wireless card is working great now! Thanks for all your help.  Now, I'm going to lament the loss of $20 that I spent to get a "linux compatible" card.  Sheesh!

---

### Post by s3a on 2007-08-21
Wouldn't it be less of a hassle to re-install?

---

### Post by tyggna1 on 2007-08-21
After how many repositories I've added, and all the configuration I already have done to get my old and crappy graphics card to run the latest and greatest (well, Warcraft 3), it would probably be more of a hassel to do an os reinstall.  

I am gonna try to get this card working in my wife's computer, though.  I have a D-link card for her computer that was built around the Prism2 driver, but it's PCMCIA (which stands for People Can't Memorize Computer Industry Acronyms) and I'd rather use the antenna that's wired around her LCD screen than the 2cm that the card provides.

<sigh> but it will still be a few days before the Dell depot sends her computer back with a new motherboard.

---

