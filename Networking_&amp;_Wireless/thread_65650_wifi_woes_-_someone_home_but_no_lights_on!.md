---
title: "wifi woes - someone home but no lights on!"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by MrCheese on 2005-09-14
I have installed a test setup of Hoary on a spare laptop & slapped in a Safecom 54108 cardbus wifi card. The system detected it on install, it is configured & visible in both ifconfig & iwconfig, however it appears to using the acx_pci module.

Although everything seems set to go the power light on the card does not come on - and hence will not detect any network when I get it near my router. 

As a last-ditch attempt I tried installing the XP driver via ndiswrapper - still no joy.
Any clues fellow Ubuntu-ers?

---

### Post by knappen on 2005-09-14
Did you get ndiswrapper to install the driver ?

What do you get when you type ndiswrapper -l ?

---

### Post by MrCheese on 2005-09-15
[QUOTE=knappen]Did you get ndiswrapper to install the driver ?

What do you get when you type ndiswrapper -l ?[/QUOTE]
 ndswrapper -l shows the driver to be loaded & the hardware present. This is my dilemma - all the signs are that it should work but it doesn't :(

I've just read elsewhere that upgrading ndiswrapper may do the trick so I'll try that tonight. However, native support is preferable and the acx_pci driver appears to do everything except actually get the card going (just like ndiswrapper), and the card certainly shows up as if it's alive when the system is queried with lspci, iwconfig etc.

---

### Post by knappen on 2005-09-15
Is the module ndiswrapper loaded?

Do a lsmod and see if it is there.

---

