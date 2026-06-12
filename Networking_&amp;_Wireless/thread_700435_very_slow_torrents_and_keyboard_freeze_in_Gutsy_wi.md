---
title: "very slow torrents and keyboard freeze in Gutsy with wireless"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Chamith on 2008-02-18
Hello,

I am having very odd problems with Gutsy after I decided to switch from a USB modem to Wireless.

Under XP my maximum speed using dslreports.com was 2008kbs.. but only 130kbs under Gutsy (and usually around 50kbs).

When using torrents (bitorrent, Azureus, utorrent, MIRO), I start with speeds of 130 but very soon the internet speed crashes (below 1kbs) AND my keyboard freezes.  After system restart, the computer and internet works fine, but any torrents still causes the freeze, etc.  <<To note, when this happens, I can still access the wireless network using my PDA and the internet works perfectly!>>

I've tried firestarter to open ports (and I've disabled the firewall on my router) but to no avail?

DESPERATELY seeking advice,
Thanks

---

### Post by Rogers on 2008-02-18
Please describe your network connection -- I'm guessing you used to be connect to the modem and now you've got a router and are using wireless.

The **ONLY** way to make torrents work well behind a router is to forward ports.  it's really easy.  Just goto 192.168.1.1 or 192.168.0.1 in firefox and forward the required ports to your machine.  I do 7777 and configure AZ to work on 7777.  Bam done.

---

### Post by Chamith on 2008-02-18
Hey, thanks for the tip...

I tried to port forward - but it was already configured (silly me) I had done it earlier for torrents to work with windows.

Torrents still work with windows, and still the same slowdown / crash / keyboard freeze in Ubuntu.

But I do not think that the keyboard freezing is related to port forwarding?

---

### Post by Rogers on 2008-02-18
It sounds like you've got a hardware issue or a driver issue.  System stability should be a constant....

---

