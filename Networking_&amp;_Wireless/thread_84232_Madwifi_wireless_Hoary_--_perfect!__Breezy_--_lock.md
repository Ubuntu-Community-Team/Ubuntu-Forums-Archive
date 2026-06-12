---
title: "Madwifi wireless: Hoary -- perfect!  Breezy -- locks up machine"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by firecat53 on 2005-10-30
I'm posting here again because after trying everything for a couple of weeks and with no responses here or on the Madwifi mailing list yet, I'm completely stumped. 

Hardware: DWL-G630, Dell Inspiron 7000.

_Problem_:  When attempting to activate wireless card either via ifup or ifconfig ath0 up, the machine completely locks up (keyboard and mouse) until I remove the card.  The entire setup worked perfectly under Hoary and I'm posting this from Knoppix with the same card!!

_What I've tried:_ 
  1. The stock breezy  networking gui.
  2. Recompiling the madwifi drivers. I used gcc-3.4 to match the kernel compiler version.
  3. Compiling an older version of the drivers.
  4. Compiling a new vanilla kernel (2.6.13.4) and then compiling the drivers. (a learning experience all by itself!)

_Pertinent Info:_
```
 ath_hal: module license 'Proprietary' taints kernel.
 ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
 ath_rate_sample: 1.2
 ath_pci: 0.9.6.0 (EXPERIMENTAL)
 ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
 ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
 ath0: H/W encryption support: WEP AES AES_CCM TKIP
 ath0: mac 7.8 phy 4.5 radio 5.6
 ath0: Use hw queue 1 for WME_AC_BE traffic
 ath0: Use hw queue 0 for WME_AC_BK traffic
 ath0: Use hw queue 2 for WME_AC_VI traffic
 ath0: Use hw queue 3 for WME_AC_VO traffic
 ath0: Use hw queue 8 for CAB traffic
 ath0: Use hw queue 9 for beacons
 ath0: Atheros 5212: mem=0x11000000, irq=11
 ath0: ath_chan_set: unable to reset channel 3 (2422 Mhz)

```
That last line "unable to reset channel 3" seems to be the only difference I can see from when it did work.  Also, I've got a PCMCIA ethernet card that works just fine, so it doesn't seem like it's a PCMCIA problem.

I really don't want to go back to Hoary! Anyone with ideas about what else could be different between Breezy and Hoary when it comes to networking? It has to be something that would affect ifconfig and ifup, because they both cause a freeze.

Thanks!

Scott

---

### Post by tjabri on 2005-11-02
Hey,

Just wanted to let you know: I'm having problems with Breezy hanging when the screen blanks to boot into X. It only does this if I enable the wireless during the previous session but works fine if I boot into recovery mode and startx from there. 

I'm currently researching a solution to this problem and will advise if I find a solution.

---

### Post by firecat53 on 2005-11-03
Well, after numerous days of banging my head, it appears the problem was due to having two pcmcia network cards inserted at the same time (one wireless, one ethernet). If I had just removed the ethernet card, the wireless would have worked from the start!!

At least I learned a lot about compiling kernels and drivers..........

However, it worked fine in Hoary to have both cards inserted. Any ideas which program would have changed between Hoary and Breezy that would cause lock-ups like that with two network pc cards?

Scott

---

