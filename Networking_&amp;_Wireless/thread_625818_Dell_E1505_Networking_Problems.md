---
title: "Dell E1505 Networking Problems"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by angel120 on 2007-11-28
I just installed Ubuntu 7.10 last night on my Dell Inspiron E1505, and without changing ANY settings, I can't connect to the internet, whether it's wired or wireless, nothing happens.

On my Home network, I have a 128bit WEP key, but Ubuntu doesn't even find the SSID on it's own, I'd have to manually type it in.  So I click "Connect to other network", and type my SSID in, I select WEP 128bit, type my key in, and keep the Authentication as "Open".  It tries to connect for a few mins, then it prompts me again for my WEP key, so I re-type it, and then it tries again for another few mins, then prompts again.  This pretty much goes on for an infinite amount of time, nothing else happens.

So, I tried a wired connection directly to my Linksys WRT54G router, and Ubuntu doesn't even recognize that.  This happened w/ both the Live CD and full installation.

On campus, we have an open network (no WEP or anything like that), and we have to sign in in order to browse the web.  This doesn't work in Ubuntu, I have the same problem as above.

I have my laptop dual-booting between Ubuntu and Vista, and Vista is able to connect to the internet, no problem.

PS - This is my first time EVER using a Linux OS, so please forgive my ignorance :).

---

### Post by edm1 on 2007-11-28
Can you open the terminal, Applications>Accesories>Terminal, type lspci and post the output.

---

### Post by angel120 on 2007-11-28
A bunch of output was returned, I'm going to skip the ones that have nothing to do w/ networking.

Host Bridge
VGA compatible Controller
Display Controller
Audio Device:
PCI Bridge
PCI Bridge
USB Controller
USB Controller
USB Controller
USB Controller
PCI Bridge
ISA Bridge
IDE Interface
SMBus
**03:00.0 Ethernet Controller: Broadcom Corporation BCM4401-B0 100Base-TX(rev 02)**
FireWire
Generic System Peripheral
System Peripheral
System Peripheral
System Peripheral
**0b:00.0 Network Controller: Broadcom Corporation BCM74311MCG wlan mini-PCI (rev 01)**

---

