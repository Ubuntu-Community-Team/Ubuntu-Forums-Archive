---
title: "Here's one...wireless samba printing strangeness"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by hokiejz on 2005-08-21
So I've got a Linux PC (file/print/cpu server) and an XP Laptop hooked up via a Netgear WGR614v1 (non-beta firmware).  Whenever I print something graphical (excel chart from a pdf file) using samba from the laptop to the pc, the Netgear immediately forgets that it's a wireless router until I cycle its power.  Doesn't even appear to broadcast its SSID.

BUT...I printed a web page (mostly text) just fine, albeit slow.
AND...when I print using IPP, it works just fine no matter what I print, and it's a LOT faster.

Tonight I'm gonig to try a large file transfer and a remote X login to see if maybe it's just the traffic volume confusing the Netgear.  Just trying to see if anyone's had a similar issue or has any suggestions.

I might just need to buy a new router if it's traffic volume killing it...this one's getting kind of old by wifi standards...who's got a brand they like?

Linux PC:  AthlonXP on ECS K7S5A motherboard
Fresh Ubuntu Hoary install
Ralink RT2500-based PCI card with rt2x00 Beta 3 drivers
Samba/CUPS set up to print octet-stream raw to my Canon s600 over USB
  ("use client driver=no" doesn't seem to show up in the testparam output...?)
  (all printing browsable, show add printer wizard=true)
  (crashed the netgear once on printer driver upload, but started over and it worked the second time)

XP Laptop:  IBM Thinkpad T41
XP SP1
new Intel generic PRO/Wireless 2200bg mini-PCI with latest drivers
  Managed by latest version of IBM Access Connections
no firewall software, but do have norton antivirus

Netgear:
b or g  (trying "b only" tonight...maybe it was getting confused?)
MAC access control
dhcp server running, but reserved fixed IP for laptop and linux pc
128-bit WEP, open

j.

---

