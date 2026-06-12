---
title: "Edimax EW-7128G Not recognised"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by phasee on 2007-07-04
Hi. I am running Ubuntu Fiesty AMD64, I have a wired connection but would like to run wireless.

I connected my wirless edimax EW-7128G card and it is picking up my network SSID but whenever I put the WEP key in it wont connect (It is the right key I have checked many times).

When I go into Applications > System > Administration > Network Tools, the wirless adapter is showing on "ra1" but is named "unknown interface"

There was something else I saw somwhere on the computer about "rt61" but I thought this device uses "rt2500" chipset, could this be the problem?

I am unsure how to rectify this.
Thanks for help.

---

### Post by phasee on 2007-07-05
does anyone know? :)

---

### Post by peterl_j on 2007-07-10
Hi

I am also having problems.

I added 

auto ra0
iface ra0 inet dhcp

to /etc/network/interfaces

and then turned security on my router.  This enabled me to get a bit further but it still does not connect.

Peter

---

### Post by peterl_j on 2007-07-10
Hi 

That should have read OFF on my wireless router.

Peter

---

