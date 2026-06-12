---
title: "[SOLVED] for some reason wireless has randomly stopped... now need to modprobe every"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Choad on 2007-07-10
ok it's this kind of thing that really let's ubuntu down. this is my mums computer, and if i wasnt here she'd be completely screwed

basically, the wireless card was set up by me a few weeks back when we got this comp. it is a w311v3 netgear pci card. needs ndiswrapper

for some reason, when i looked at it this morning it was not in roaming mode, but instead it was fixed on our netgear router. i changed it back to roaming mode, it worked fine, restarted a while later and its gone totally

now it only works if i sudo modprobe ndiswrapper. i have done sudo ndiswrapper -m but it says its already got the module files sorted

help?

---

### Post by t4thfavor on 2007-07-10
add the module name to /etc/modules  and reboot.

---

### Post by Choad on 2007-07-10
thanks... that did it.

---

