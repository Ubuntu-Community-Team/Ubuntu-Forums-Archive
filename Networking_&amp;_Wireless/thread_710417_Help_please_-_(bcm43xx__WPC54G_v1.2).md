---
title: "Help please - (bcm43xx / WPC54G v1.2)"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by ind on 2008-02-28
I'm installing Ubuntu on a notebook that is using a Linksys WPC54G v1.2 wireless card. Upon install, I'm receive the following text on screen. The install does not complete.

I've previously tried the older (6) version of Ubuntu, and the wireless card didn't work, but at least Ubuntu installed. I'm going to try installing it with the card unplugged, but would really like to get the card working. I've found a few guides (such as HOWTO: Broadcom 43xx etc) and I will try those.

Any ideas on the below as I progress towards a solution?

cheers,

_______________________________
[B]*Starting deferred exceution scheduled atd [OK]
*Starting periodic command schedule crond [OK]
*Checking battery state [OK]
*Running local  boot scripts (/etc/rc.local) [OK]
[   120.984000] bcm43xx: Error: Microcode "bcm43xx.microcode5.fw" not available or load failed.
(about a 1-2 minute pause until the next line)
[   367.764000] bcm43xx: Error: Microcode "bcm43xx.microcode5.fw" not available or load failed.
(about a 1-2 minute pause until the next line)
[   489.808000] bcm43xx: Error: Microcode "bcm43xx.microcode5.fw" not available or load failed.[/B]
_______________________________

---

### Post by ind on 2008-02-28
UPDATE 1: Desktop CD continued to hang at the following:

*Starting deferred exceution scheduled atd [OK]
*Starting periodic command schedule crond [OK]
*Checking battery state [OK]
***Running local boot scripts (/etc/rc.local) [OK]**

(screen flickers, eventually HDD stops and screen blank)

Successful install with ALTERNATIVE CD. Will update status on WPC54G card. During the install, the system has identified two network devices as:

BCM4401 eth0 (wired)
BCM4306 eth1 (wireless)

---

### Post by ind on 2008-02-28
While reviewing the list of supported wireless cards, I came across the following information regarding my card; however, the instructions confuse me. They state that when Ubuntu starts, I should open the restricted drivers management and enable bcm43xx. How do I do this?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

Linksys
WPC54G (ver 1.2)
Broadcom (BCM4306 rev3)
?
?
Yes (after fix)
No

Get recognized in the setup process, but unable to use it. After setup completes, the card is shown in the network interfaces (as eth0, all hardware details are shown too), but the system is unable to activate it. Updating the firmwares (link broken) fixes the problem. **_To do this when Ubuntu starts, open the restricted drivers management and enable bcm43xx.	_**

2006-03-14
PCMCIA


EDIT - darn, the install looked like it was working and then I get a black screen when it's finished.



RESOLVED

---

