---
title: "DWL-G650M (atheros AR5005VL) and Madwifi: Or just 'Asking for a Miracle'"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by anasofiapaixao on 2007-05-16
EDIT: From [http://madwifi.org/wiki/ngFeatures](http://madwifi.org/wiki/ngFeatures) I read this:
> **Enhanced Chipset Support**
The HAL that comes along with the new code now supports almost all of chipsets that are currently available. There should be a new HAL soon which supports all of them except for USB chipsets.

So that's good news. I tprobably means it won't be long until a version supporting this card coming out. All I can tell is that as of now, May 24 2006 with the latest snapshot, the card is still not detected, but
```
lspci | grep Atheros
``` returns > 04:00.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01) (as it always did) and
```
dmesg | grep ath_hal
``` returns > [   22.648000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
and no error 13. Can we maybe hope?...

Well, I bought a D-Link DWL-G650M wireless card on purpose to use with aircrack. I thought about the G650, but apparently every revision has a completely different chipset Oo and I don't really like lotteries. Anyone who tried to use aircrack with a wireless card with the AR5005VL Atheros chipset is provbably already feeling my pain...

Well, as windows drivers (and consequently ndiswrapper) don't support monitor mode all I can hope is that some day the HAL will support this chipset. What I'm asking is whether anyone heard anything from anyone who may thought has heard some rumours on this chipset being in plans of being supported by the guys who do do the Atheros HAL!...

---

### Post by B-Con on 2007-05-19
I just got a DWL-G650 and I can't even get monitor mode to work under Feisty no matter what I do, which is weird since monitor mode works for my Intel 2200BG right out of the box.

Networking has been nothing but a pain since I switched to Feisty.

---

