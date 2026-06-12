---
title: "NetworkManager on crack under gutsy. Haaaalp!"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by |{urse on 2008-11-27
Hi there. I'm having this really odd problem with NetworkManager under Gutsy (no, i don't want to to upgrade to hardy or intrepid) Anyways, NetworkManager will use a ridiculous amount of cpu. top usually reports it using anywhere from 50 - 100 percent at times. It seems this only happens when i lose signal. For some reason when NetworkManager gets this out of hand i can only kill it like this:

```
#!/bin/bash
gksudo killall NetworkManager
gksudo killall nm-applet
gksudo NetworkManager
nm-applet
xmessage -center "Hi, `whoami`. Click the button." -buttons "Restart NM":0]
gksudo iwconfig ath0 essid "linksys" || gksudo iwconfig ath0 essid "Jayhawk"
exit
```

by the way.. linksys is never weak enough that the script has to resort to the Jayhawk essid. However, when i start this box the normal way with the default gutsy session my connection to linksys is tenuous at best.
I'm not usually one to write scripts for such simple things but for some odd reason this is the only way i can get the wireless working again once it has "died". It may also help to note that restarting the networkmanager via dbus (sudo /etc/dbus-1/event.d/25NetworkManager restart) does not help. the situation at all.

There are only 2 reasonably strong signals nearby but i know they arent weak enough to cause NetworkManager to have to reconnect constantly. Any help would be much appreciated and thanks in advance ^^

---

### Post by |{urse on 2008-11-27
heres the only relevant excerpts of "dmesg | more" i could find. Just initialization stuff.

> [   37.914993] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 1
2 14:12:24 PDT 2007
[   37.994623] wlan: 0.8.4.2 (0.9.3.2)
[   38.016694] input: PC Speaker as /class/input/input2
[   38.044292] ath_pci: 0.9.4.5 (0.9.3.2)
[   38.044383] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ
 22
[   38.690990] ath_rate_sample: 1.2 (0.9.3.2)
[   38.692764] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   38.692772] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 1
8Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   38.692783] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54M
bps
[   38.692791] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   38.692796] wifi0: mac 7.9 phy 4.5 radio 5.6
[   38.692802] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   38.692804] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   38.692806] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   38.692808] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   38.692810] wifi0: Use hw queue 8 for CAB traffic
[   38.692812] wifi0: Use hw queue 9 for beacons
[   38.694708] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   38.717782] wifi0: Atheros 5212: mem=0xfe400000, irq=22


---

### Post by |{urse on 2008-12-03
bumpity

---

