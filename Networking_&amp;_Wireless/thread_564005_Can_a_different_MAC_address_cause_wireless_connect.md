---
title: "Can a different MAC address cause wireless connection problems?"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Depressed Man on 2007-09-30
A while back, my laptop was working fine in wireless with WPA encryption on my router. However it began not connecting. I recently installed WICD on Gutsy and realized that the MAC address it says my router has differs by one value. 1A instead of 1B (which is what the router has).

Could this be causing my connection problems? Everything else is fine (password, encryption, etc..) (and it connects fine in Vista).

---

### Post by noob12 on 2007-09-30
Note that a wireless router will generally have two MAC addresses: one for wireless and one for the wired interface.  The output of **sudo iwlist scan** shows the wireless one.   Plugging in and doing an **arp** on the ip address of the router will give you the wired one.  The configuration interface on the router may have a two different pages which display them.

---

### Post by Depressed Man on 2007-09-30
Well I tried changing the MAC address and it didn't work. :(

disabled hide SSID and it works now.. strange.

---

