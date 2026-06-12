---
title: "Network card missing after cloning hard drive"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by peterhocking on 2013-09-21
Hi

I'm running Ubuntu desktop 12.04 64 bit. Today I cloned the boot drive in my computer, removed the original boot drive & fitted the drive I'd cloned the original to. It boots up OK, except that while booting I get an error message about waiting for the network. After it has finished booting, the network connection is missing.

Opening a terminal window, if config only reveals the loopback interface, but running lspci -vv reveal the hardware details of the built in network card, (Realtek RTL 8111 etc. Running sudo ifup eth0 does nothing, doesn't even generate an error message. If I comment out the relevant entry in /etc/udev/rules.d/70-persistent-net.rules, when the computer reboots, the entry is recreated, but the network card still does not function.

The light on the port of the hub it is plugged into does not light up.

I've Googled extensively, (on another PC), but have not been able to resolve the issue.

Can anyone offer a solution?

TIA

Peter

---

### Post by peterhocking on 2013-09-21
Hi

I've looked a little further. Running sudo lshw -class network in a terminal windows shows the network card, but the first line of the response is *-network disabled.

Peter

---

