---
title: "Dell Inspiron 9100 - Broadcom BCM4306 Problems"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by joypunk on 2006-07-28
I'm having a heck of a time getting this wireless card (Dell Truemobile 1350 Mini-PCI Wireless, aka Broadcom BCM4306) to work with Ubuntu 6.06. I've tried probably 20 different guides with and without ndiswrapper. Nothing I've done has been able to work. In fact, every method I've tried has ended in 1 of 2 scenarios.

Scenario 1:
iwconfig will show eth1 as my wireless device, however, the only thing I am able to change is the ESSID. All other commands won't have any effect. Also, the Access Point is listed as "Invalid" in this scenario.

Scenario 2:
No wireless device appears to be installed. No wireless extensions are found by iwconfig, and my device doesn't even show up in the Device Manager. This is the scenario I get whenever the guide I follow tells me to blacklist bcm43xx.

I am completely new to Linux, and don't really have a clue where to look next. I've been trying to get this wireless adapater working for well over a week now.

Does anyone have any suggestions? I'd be glad to provide any other information you need. You just need to walk me through how to get you that information.

---

### Post by Zelut on 2006-07-28
I use the native bcm43xx driver on my notebook and it works fine (also 4306).

I simply install the 'bcm43xx-fwcutter' package (sudo aptitude install bcm43xx-fwcutter).  Followed this with:
/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

After that I configured my device & it worked..

---

### Post by joypunk on 2006-07-28
I was finally able to get things working using [this guide]("http://ubuntuforums.org/showthread.php?t=201902").

---

