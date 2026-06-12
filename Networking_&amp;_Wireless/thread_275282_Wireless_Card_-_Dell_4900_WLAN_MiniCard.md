---
title: "Wireless Card - Dell 4900 WLAN MiniCard"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by codecraig on 2006-10-11
hi,
  I have a Dell Latitude D820 with a Dell 4900 WLAN MiniCard.  I just installed Kubuntu 6.0.6 as a dual boot setup with win XP pro.
  I am unable to "enable" the network card.  I go to the network settings window, switch to "administrator" mode, and then try to 'enable' the wireless card on eth1....but it never becomes enabled.  I have downloaded the driver for the card for Windows (as dell only has drivers for Suse and Red Hat 8 & 9).  Other articles mention somehow being able to use the Windows driver to get it setup in Kubuntu...but I have had no luck.
  Any idea??

Thanks!

---

### Post by codecraig on 2006-10-11
Ok, in Kubuntu terminal I typed...

iwconfig

and it appears that eth1 is my wireless, but shows up as Broadcom 4311 (in windows it says its Dell 4900....)

Anyway...hope that helps diagnose my problem.

thanks.

---

### Post by codecraig on 2006-10-11
ok its actually a BCM4310, at least that's what this command output:

lspci | grep Broadcom\ Corporation

---

