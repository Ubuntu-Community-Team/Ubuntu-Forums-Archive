---
title: "restricted-manager broadcom often selects loopback for ip"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2007-08-23
I am currently using Feisty with the restricted manager loading the firmware for my Broadcom bcm4318 (fwcutter method).

This is an intermittent issue:

Networking often selects some odd IP, I am thinking it is the loopback address, as the wired lan (not connected) shows a similar address of 169.blah.blah.blah rather than 192.168.other numbers.  It isn't even connected so I don't know why it is attempting to give it an IP.

The only way I can get it to discard reconnecting to this annoying ip is to disable BOTH of the devices, have them NOT enable at startup, then enable them after a reboot.

I have tried manually adding an IP (wireless still would not connect) but it sort of defeats the purpose of being able to roam.

Would going back to ndiswrapper as I had in Edgy be a possible solution (it always worked)?

---

