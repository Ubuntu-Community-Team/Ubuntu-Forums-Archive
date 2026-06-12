---
title: "Getting started (wireless network)"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by SargeBurns on 2011-04-18
I've finally got around to giving Linux a proper go now, and I've had a few problems, all of which seem to be connected to missing drivers (I think) as my graphics get screwed up unless I boot into failsafe graphics mode via the recovery version of Ubuntu Netbook.

Anyway, my plan is to try and update/repair my graphical drivers once I've got my network connection back up and running. Hence this post - my netbook uses an ASUS 802.11g card and from what I've read, lspci -v gives the info you need to tell me how to fix my 'missing firmware' problem:

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. A6U notebook embedded card
    Flags: bus master, fast devsel, latency 64, IRQ 22
    Memory at feafc000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

So... I'd appreciate help in trying to work out how I can fix my wireless to work with Ubuntu. Bear in mind I'm completely new to Ubuntu and mostly new to Linux so apologies if I seem thick.

I can get a wired connection if needs be but I'd prefer to download wirelessly via windows and transfer over files by USB stick if I can...?

Thanks in advance for any and all help.

---

### Post by Locke_99GS on 2011-04-18
Open a terminal window (use Ctrl+T, -OR- plow through your menus and find Termianl) and install the *b43-fwcutter* program. This will setup the proper firmware for your card automagically.

```
sudo apt-get install b43-fwcutter
```

Follow the on-screen instructions. Afterwards, run *jockey-gtk* and enable/re-enable your Broadcom drivers.

```
gksudo jockey-gtk
```

Afterwards, reboot -OR- remove and reinsert the b43 kernel module. Beginners should be happy with just rebooting.

It *should* just work afterwards.

---

### Post by Pathman on 2011-04-18
I was having the same problem so did what you suggested and now it says I'm connected but I still can't access the web
Any other assistance would be appreciated

---

### Post by SargeBurns on 2011-04-19
Ok, I got there in the end! Typing this online via my Ubuntu version of Firefox!

This site was very helpful for me:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

This one was less useful itself, but pointed me to that one and another:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

