---
title: "Wireless + Edgy.   Now it works!  Why?"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by skate1 on 2006-11-09
Hi All,

I installed Ubuntu / Edgy onto an IBM Thinkpad T20 about 1 week ago.  Everything works great, except Wifi.  I have tried Netgear MA401 card, and a Lucent/Agere Orinoco Gold card.  Both cards are 802.11b, as is my Access Point.

Until today, I have never had Wifi working with my HDD install.   I have had some success using Wifi with the Live CD, but it was not reliable.  By not reliable, I mean that sometimes the card would associate and DHCP ok, and other times it would only associated, but not DHCP.

Anyway, fast forward to this morning.  After several reboots, the Orinoco card is working on the HDD install.

I have not changed anything.  No changes to /etc/network/interfaces.  No changes to BIOS, no changes to any config.  Just the reboots.

So my question.  What could cause this?

And more importantly, before I lose the connection.  **What should I check in terms of drivers, error logs, messages, etc...  to narrow down why it worked this time vs previous times.**

Thanks!

---

### Post by FrodoB on 2006-11-09
It may well be that the reboot was all that is involved here.  There are several versions of Linux that will not see an Orinoco Gold at install, but see it after a reboot.

Is is connecting to an access point that is using WEP and so forth, or has it just found an open network nearby?

At any rate it should be working with Ubuntu out of the box after a reboot. Very reliable card with Linux, buy it a gold plated storage box and hold on to it.

---

### Post by skate1 on 2006-11-09
The network is an open network.  No WEP or other security.  I live in a somewhat rural area, and am the only Wifi signal in the area.  My scanning SW (on my other WinXP laptop) verifies this.  I have several other 802.11b PCs/peripherals in the house that have no problems gaining access to the network.

I have probably rebooted my Edgy laptop at least 50-100 times.  Out of all these powercycles, I have gotten Wifi to work with the LiveCD probably 5 times, and only once with the HDD install.

Since the Wifi started working with the HDD install, I still have not power cycled.  (I am afraid to do so, as I am almost certain it will require another 20 power cycles to get it working again).

Bizarre stuff.  I suspect some kind of timing dependency during the boot process.  There probably are error logs to be examined, but frankly I do not know enough about Linux to know which logs to examine.

---

### Post by jasonerik on 2006-12-07
Hi skate1, it's been about 3 weeks now since your last post on this thread. Have you figured out why your wifi networking is intermittent and apparently unpredictable?

I'm experiencing the same problem, both with the LiveCD and now after installing Edgy Eft to my HD.

Thanks for any tips to resolve this.

Cheers, Jason\\

---

### Post by skate1 on 2007-04-26
Nope.  Never figured out why.  I have just learned to live with the ~10 reboots required before the Wifi connection associates & DHCPs.

Once I have it up and running, I try not to reboot...  It is a pain, but fortuantely, the laptop in question is used as a 2ndary desktop PC in the home, so I can live with not rebooting.

If it was being used for mobile computing, this would be unbearable.

---

