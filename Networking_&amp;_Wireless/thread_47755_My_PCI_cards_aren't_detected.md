---
title: "My PCI cards aren't detected"
date: 2005-07-09
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2005-07-09
Hi, I just put Ubuntu on an old PC of mine (Pentium 133mhz, 64 megs RAM). I have two network cards plugged into the PCI slots on the motherboard. One is a 
D-Link DWL-G520 wireless card (Atheros AR5002 chipset), and the other is a generic 3Com Ethernet card. First, during installation Ubuntu failed to detect any network interfaces. Now, lspci doesn't show either of them. I know that the drivers for these cards are already loaded into Ubuntu, and even if they weren't, lspci should still be able to see them, right? Where's the error here and how can I fix it?
Thanks.

-Jake

---

### Post by aggiechemist on 2005-07-09
This is just a guess, but I would try only doing one at a time. I have had some wierd PCI conflicts in the past and just putting only one card in fixed me up. I have no idea why, but maybe it could help.

---

### Post by otakuj462 on 2005-07-09
I just tried that with both, rebooting the system with only one of the PCI cards in and running lspci. It still didn't see them, but the "Power" LED on the back of my wireless card went into a slow blink, whereas before, I think it was just dead. Very strange.
Any other ideas?

-Jake

---

### Post by otakuj462 on 2005-07-10
Nevermind, I fixed it. Haven't gotten both cards to work, but the wireless card is now seen by lspci and I'm able to configure it. Got it to work just by futzing around with it.

-Jake

---

