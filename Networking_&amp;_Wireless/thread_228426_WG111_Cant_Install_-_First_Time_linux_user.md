---
title: "WG111 Cant Install - First Time linux user"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Cooleo on 2006-08-03
Yeah, Ive followed a tutorial,but when i do " ndiswrapper -L " It says my netgear driver is invalid, and when i do " modprobe ndiswrapper " It says 'FATAL cannot instert NDISWrapper'

Please Help, I dont want to go back to windows.

Mike

---

### Post by cantormath on 2006-08-03
> **Cooleo said:**
> Yeah, Ive followed a tutorial,but when i do " ndiswrapper -L " It says my netgear driver is invalid, and when i do " modprobe ndiswrapper " It says 'FATAL cannot instert NDISWrapper'

Please Help, I dont want to go back to windows.

Mike

Are you absolutely sure that your Wireless card will not work without Ndiswrapper.  Ndiswrapper is supposed to be a last resort.

What kind of card is it, PCI, USB?

open terminal and type
sudo ifconfig
what does it say, does the card show up at all.
next type
sudo iwconfig
what does that say? Does do you see your wireless card there?

---

### Post by Cooleo on 2006-08-03
Its USB, Under ifconfig, It comes up with loads of things like:

Link Encap: Local Loopback
inet: 127.0.0.1 
mask: 255.0.0.0

and Iwconfig it says:

lo No Wireless Extentions
sit0 No Wireless Extentions

Does that help?

Mike

---

