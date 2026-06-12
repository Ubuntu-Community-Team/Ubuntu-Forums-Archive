---
title: "Acer Aspire 5102 wireless card."
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by Gravesent on 2007-05-01
For a few days I've been trying to get the wireless card from my laptop (acer 5100 series) to work, I read some tutorials here but so far I've had no luck, I used ndiswrapper to install a number of drivers but it's not working..

First of all I haven't been able to discover the exact wireless chipset model.. if any of you have the same laptop and know I'd appreciate it..

So far I've installed acers drivers for windows XP from the acer website and the vista drivers that came with the laptop, only with vista's drivers did I see any result, but even though I see a driver in ndiswrapper it says "hardware present:NO" with any other driver I see nothing..

---

### Post by unisol on 2007-05-01
i believe you have the atheros chipset. i think if this is the case, you  could try madwifi drivers. post the output of these commands;lspci,
sudo lshw -class network, and
iwconf.

---

