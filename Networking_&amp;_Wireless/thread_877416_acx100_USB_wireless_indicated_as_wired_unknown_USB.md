---
title: "acx100 USB wireless indicated as wired unknown USB"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by MaxPowers on 2008-08-01
Hellooo,

I've just reinstalled Ubuntu to Hardy,

I have an internal Atheros wireless PCI card,
which works perfectly (ath0, madwifi-ng drivers)

but now I wanted to test my USB D-Link DWL-120+ adapter (the Windows D-Link app does not support WPA):
chipset: acx100,
Hardy does not seem to support it out of the box:
wired unknown USB

not even the interface is there,
only ath0... nothing about acx...

only when I check USB info, D-Link is listed (where u only see manufacturer info)

so I tried to install the drivers manually:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

tried the patch...
[http://acx100.sourceforge.net/wiki/Patch_2.6.22](http://acx100.sourceforge.net/wiki/Patch_2.6.22)

verified that the firmware images exist,

disabled Network Manager (but then internet did not work anymore, iwconfig still only listed the ath0 interface...)

is it because only 1 wireless interface can be active?
or is it because of incompatibility with Hardy?

in that patch file I only see PCI, nowhere USB, could it be that those drivers only support PCI, and not USB?
there are 3 versions of the driver, which one is best here?

anyone a clue?
many thanks in advance for any help...

Kind regards!

---

### Post by MaxPowers on 2008-08-04
I've installed Xubuntu on my old laptop (500 Mhz),
in the pcmcia slot is a Xircom ethernet Lan cardbus,
on USB the D-Link wireless adapter (DWL-120+, acx chipset),

and out of the box it also says 'Wired unknown USB...' ...

haven't had the time to install the drivers manually,
but I doubt it will make any difference...

really nobody can help me?

thanks anyway,

Regards...

---

