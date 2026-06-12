---
title: "Help with my DWL-650+"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by synd7 on 2006-09-16
ok, Ive hot a DWL-650+ that refuses to work, I've read that this particular card should work out of the box but it doesnt for me.

The card is recognised by the laptop (quite an old one) and the link light glows a healthy green. In the networking settings it cannot see my router, even when its only 2m away.

I've tried "sudo iwlist wlan0 scan" and it finds nothing.

And i'm using Xubuntu if that helps at all.

Any Ideas?

---

### Post by lawcox on 2006-09-16
I have this same card and it worked for me just about right out of the box with WEP.  It is not compatible and does not work with network-manager-gnome, so you have to use the other manager to configure it.

---

### Post by tturrisi on 2006-09-17
The issue w/ the dwl 650's is that dlink made them at various times using 4 different chipsets.  You need to find out what chipset the card has.

---

### Post by synd7 on 2006-09-18
Its a DWL-650+ so its got the atheros chipset i think.

What network manager should i use?

---

### Post by tturrisi on 2006-09-18
Use net-admin, the networking applet that comes w/ Ubuntu.  System > Administration > Networking

To use Atheros chipset cards you need the madwifi drivers:
1. enable the universe/multi-univers repositories in Synaptic.
2. install linux-restricted-modules that match your kernel.

Some dwl650+ cards have a different chipset & use these drivers:
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

---

