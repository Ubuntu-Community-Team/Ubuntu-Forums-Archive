---
title: "Help with Microsoft wireless notebook adapter"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by lussypips on 2007-01-28
Ok, here's the deal:

I've had the Microsoft MN-520 working before.  It hasn't worked since I tried to install Fedora then put Ubuntu back on the laptop.

The card uses the Orinoco drivers; there are loaded.  

I have check, checked, rechecked, then just for good measure check the security settings to make sure I was setting it up correctly.  Ifconfig shows the card and iwconfig show the card but when I try to bring the card up it will not get an IP.  I tried with an open AP but it still didn't work.  Oh, and Gnome network manager doesn't show the wireless int for some reason.

I've found a how-to which suggested adding some info to /etc/pcmcia/config.  Well, /etc/pcmcia/config doesn't exist and when I add it with the info that was suggested to add, the PCMCIA card does not work at all--no link lights or power light.  There is a /etc/pcmcia/config.opts but adding the card's info to that didn't help at all.

I also followed a how-to that suggested installing wpasupplicant.  No luck!

Any ideas?


Thanks,
Lussy

---

