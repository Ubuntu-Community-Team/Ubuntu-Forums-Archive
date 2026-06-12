---
title: "Network Card worked but doesn't anymore"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by beaucollins on 2005-07-30
My network card worked upon installing Ubuntu Hoary Hedgehog.

I was however having problems with my sound card (only producing fuzz).  I found a forum thread that fixed it.  Ufortunately I can't find the thread again.

It seemed, though, that after I fixed the sound, the network card stopped working.

The network card is in a PCI slot and the sound-card is built-in.

I get lights on the back of the network card and on the router, but no activity flashing.  I don't think I get assigned an IP address either where I was before.  I've try disabling and reenabling the network card through the admin interface but nothing happens.  After several shutdowns and reboots the problem still exists.  I'm ready to scrap the install and do a clean install but would rather not.

Any ideas?

---

### Post by kleeman on 2005-07-30
What is your network card?

What does 

sudo ifconfig

give?

What is in /etc/network/interfaces

---

