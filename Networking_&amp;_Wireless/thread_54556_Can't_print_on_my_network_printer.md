---
title: "Can't print on my network printer"
date: 2005-08-05
forum: Networking &amp; Wireless
---

### Post by madnoh on 2005-08-05
Hi everyone,

I have a Ricoh Aficio 270 PCL printer connected to my office network, IP address: 10.0.0.4.

I tried adding a new printer at the System Menu> Administration > Printing. Set it up as ipp://10.0.0.4 and used the Aficio 220 driver. When I tried to print a test page I get this message in the General tab  :

Paused: Destination printer does not exist!

I'm a newbie at Linux. Can anyone tell me what I'm doing wrong? Any help on this would be much appreciated.

By the way, I'm on Hoary 5.0.4 running on a Pentium 4 and all the other PCs are on WinXP (if that bit of info helps).

Thanks in advance.

---

### Post by manicka on 2005-08-05
Is this a stand alone network printer or a printer attached to one of your xp machines and shared across the network?

---

### Post by madnoh on 2005-08-05
It's a standalone network printer with its own static IP address (10.0.0.4).

Strange thing is, when I used Knoppix 3.4 it works.

Cheers.

---

### Post by madnoh on 2005-08-06
Okie dokie.. I downloaded KDE and it works. Perhaps I have to update the CUPS package when using GNOME or something.

---

