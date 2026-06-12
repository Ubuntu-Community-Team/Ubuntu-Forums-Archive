---
title: "Wireless Not Working"
date: 2019-09-09
forum: Networking &amp; Wireless
---

### Post by cfung on 2019-09-09
I installed lubuntu today clean moving away from Windows. Never used or worked with anything Linux before.

I installed via a USB and during the install process I had to connect to wireless internet to finish the install. Once I reset the wireless no longer worked even though I didn't change any settings.

Have read most of what I could Google but didn't find anything that answered this specific problem.

Laptop is an ASUS Transformer.

Any help is appreciated.

---

### Post by guiverc on 2019-09-09
You haven't told us your release of Lubuntu, or the specifics of your problem, but I'll provide the following 

[https://manual.lubuntu.me/3/3.1/3.1.5/nm-tray.html](https://manual.lubuntu.me/3/3.1/3.1.5/nm-tray.html)

(the manual page for Lubuntu and how to access wifi).

Providing your release, plus more specifics as to your problem, or how far you got with Ubuntu troubleshooting (eg. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)) is helpful in us providing more assistance to you.  Is your wifi hardware recognized?  this can help determine this; Lubuntu manual assumes it's already recognized.

Official docs provide details to read your actual chipsets used by your hardware which then allow google & search engines to be super useful (far better than a brand/model of box that may have up to 8 chipsets used during its production unless it's a *once-off* production model).  I usually add "*site:*.ubuntu.com*" to my searches to limit results to official sources; removing that restriction only if I can't find what I want (though it can be harder with flavors, eg. you have to know **lubuntu.me** is the lubuntu web site where as google can send you anywhere).

---

### Post by pcfan1234 on 2019-09-10
For internal WiFi cards show
```

lspci

```
We need to know what chipset you have.
Please post the output of every command here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by cfung on 2019-09-10
**Lunbuntu Info**
LXQt Desktop Toolbox - Technical Info
LXQt About Version:     0.14.1
LXQt Version:           0.14.1
Qt:                     5.12.2
Build type:             Release

**Wireless N**[B]etwork Info
[/B]description: Wireless interface
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0f0
       version: 00
       serial: ec:0e:c4:29:0a:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=mt76x0e driverversion=5.0.0-13-generic firmware=1.0.07-b370 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7800000-f78fffff[B]


What I[/B] [B]Have Tried So Far
[/B]Followed the steps from user Pilot6 in the below link but that led to my wired connection no longer working so I had to reinstall everything from scratch so I'm hesitant to try anything else based on forum responses since I can't find anything specific to lunbuntu

[https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working](https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working)

---

