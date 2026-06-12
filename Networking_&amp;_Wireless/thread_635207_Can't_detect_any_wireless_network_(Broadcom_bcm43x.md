---
title: "Can't detect any wireless network (Broadcom bcm43xx)"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by re2st on 2007-12-08
I tried to post this on the super-long sticky post on Broadcom 43xx, but it's impossibly buried down to the last page I'm afraid nobody would even notice it.. :(
Anyway, I created a new post so it would get a better exposure
Sorry if this is not appropriate

HELP!!!!

I got the wireless thing on (the light is blue and all), but I still can't see any Network (while I can on my Windows PC).

I'm using Compaq Presario V6500Z,

lspci gives me this:
```
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

lspci -n gives me this:
```
03:00.0 0280: 14e4:4311 (rev 02)
```

Network Manager Applet shows "Wireless Network" but nothing underneath it.

iwconfig eth1 gives me this:
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

when i tried sudo iwlist eth1 scanning, it gives me this:
```
eth1      No scan results
```

I installed the bcm43xx driver using Restricted Driver Manager and have tried both the provide URL (the .de domain URL) and downloading the wl_apsta file from Wiki).

what gives/ I can't figure out what's wrong.

I literally am screaming for HELP now.. :((

---

### Post by alexmoon on 2007-12-29
I'm having the same problem. I have a Broadcom 4306 card, and the bcm43xx drivers for it seem to be installed. 
[B]
iwconfig[/B] gives:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"DLINK"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


But neither network manager nor wifi radar seem to be able to detect my home network (which has WEP), even when other people can connect from Windows. 

**iwlist scan** returns:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by insertAlias on 2008-01-03
I also have a similar problem, but mine only started when I updated to the development release.  With Gutsy, it worked fine, but in Hardy, I can't detect or connect to any networks.  I have the Broadcom 4401, and the Firmware for Broadcom 43xx chipset family worked before.  Now it does not.

---

### Post by berthiggins on 2008-01-03
Hi for the guys using Gutsy I would try using the windows drivers through Ndiswrapper 
you can use the windows driver that came with your card/pc
for the guy that is using hardy bcm43xx is not used on the hardy kernel you need the new b43 driver and firmware ( I have tried ndiswrapper with this kernel but it does not seem to work)
I  have a bcm4318 and have tried all these drivers the ndiswrapper solution has always been fasterand more stable, I try the open drivers every so often as I would prefer to use them when they work better.

This link for the new b43 driver (read the bit after kernel install) [http://ubuntuforums.org/showthread.php?t=646755&highlight=gutsy+hardy+kernel](http://ubuntuforums.org/showthread.php?t=646755&highlight=gutsy+hardy+kernel)

Here ia a howto for ndiswrapper ( there are many) [http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

Any more info needed ask and I will help if I can :)

---

### Post by metoor30 on 2008-01-03
The default module for the broadcomm cards never work.  Follow the following HowTo (Option 2).  ndiswrapper will allow you to use the windows drivers as a module.  I have a broadcomm bcm4306 and I can connect to my WEP wireless connection at home and my WPA connection at work.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcomm](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcomm)

---

### Post by ...Max... on 2008-01-03
...except it's no guarantee of success :( I've tried just about every approach google uncovered for me to no avail ([http://ubuntuforums.org/showthread.php?p=4064688#post4064688](http://ubuntuforums.org/showthread.php?p=4064688#post4064688)). From the look of things, 43xx chipsets are still problematic for lots of ppl. I'd sure love to see the resolution for MY problem though :)

---

### Post by rustybronco on 2008-01-03
> **metoor30 said:**
> The default module for the broadcomm cards never work.  
Yes they do... 
[http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)
[http://ubuntuforums.org/showpost.php?p=3749763&postcount=5](http://ubuntuforums.org/showpost.php?p=3749763&postcount=5)
bcm4318-v2 pci, and with a bcm4318-v2 pcmcia

---

### Post by insertAlias on 2008-01-03
Thanks, the b43 driver fixed my problem.

---

