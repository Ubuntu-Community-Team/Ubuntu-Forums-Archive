---
title: "Network printing HP F4280"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by absolutezero1287 on 2008-09-29
I recently bought an HP F4280 and it's working great. I got all the necessary software for HP printers. Ubuntu autodetected the printer and tested it as soon as it was plugged in. It was added automatically. In short, it worked perfectly.

Then I began to think...everyone at home is going to be asking me to "print this" or "scan that" for them. How can I make my new printer into a network printer?

There's a wireless G network at my home. With the router connected to my PC via a Cable modem. 
Router is Linksys Wireless G WRT54G.
The other computers get internet via a Wireless-G USB Adapter WUSB54GC.

I just wanted to know if it's possible to configure my network so that people can request a printing job from another computer and have it print in the main computer (my computer).

---

### Post by cariboo on 2008-09-29
You need to install samba to share your printer with the rest of the computers on the network. Have a look at this guide for specifics:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

This will walk your through anything from a small home network to a large company network.

Jim

---

### Post by absolutezero1287 on 2008-09-29
Thanks but that seems like it's overkill. It looks as if its more geared towards setups at an office or corporation.

All I wanna do is get one computer to communicate with mine in terms of printing. Does the other computer have to have samba installed too? Also, it's running XP.

---

### Post by absolutezero1287 on 2008-10-17
Bump

---

