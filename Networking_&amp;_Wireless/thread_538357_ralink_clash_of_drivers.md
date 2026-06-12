---
title: "ralink: clash of drivers"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by m0untainrebel on 2007-08-29
i have an averatec 2300 series laptop, and the onboard wireless card has a ralink chipset. a fresh install of ubuntu feisty recognizes the card automatically and uses the rt73usb module. with the rt73usb driver, network-manager can scan networks correctly, but fails when trying to connect to any.

so i blacklisted rt73usb and used ndiswrapper with the driver that came with the laptop (i end up using a file called rt73.inf), and this works better. network-manager lets me connect to WEP and WPA encrypted networks, but i have to go through network-admin (the old way, before there was network-manager) to connect to open networks for some reason. that's what i've been doing.

anyway, i just bought a new usb wireless card that uses the rt2570 driver. this is where things get weird. when i have the rt73usb module blacklisted and ndiswrapper running, and plug in my new usb wireless card, it seems to work fine. network-manager recognizes it and lets me connect to any network. but running airmon-ng, i found that my usb card was actually just using ndiswrapper as well (probably the same rt73.inf driver), so it wouldn't let me put it in monitor mode. also what's weird, is when i try booting up with my usb card plugged in, things get really laggy and it ends up doing a hard crash pretty much every time- it only works when i plug it in after booting up.

i don't want to use ndiswrapper for my new wireless card, i want to use rt2570. so i blacklisted ndiswrapper, to just disable my onboard card (for some reason my bios doesn't have an option to disable it), but then when i plug in my usb network card it crashes. i tried unblacklisting rt73usb (so my onboard card would use broken drivers, but i would just use my usb one with working rt2570 drivers). ubuntu recognizes both network cards when i do this, and it doesn't crash either, but neither of them even scan for networks correctly.

something really weird is going on, and i think it has to do with the fact that i have two different ralink wireless cards with similar, but not the same, drivers (but apparently the same windows driver works for both with ndiswrapper). i can't disable the onboard wireless card from the bios, and really what i want is to be able to go in monitor mode with my new usb one- plus, my usb card has an external antenna port, which is a big plus.

if anyone has any ideas of things i could try, that would be great. thanks.

---

