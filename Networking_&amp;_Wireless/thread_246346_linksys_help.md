---
title: "linksys help"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by peav007 on 2006-08-29
i have a pci linksys wireless card installed in my computer.
now the problem is this
0000:01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


Installed ndis drivers:
bcmwl5  invalid driver!
*xxx.ini*       invalid driver!
my question is how do i remove both of these files so i can have ago at reinstalling the driver for the card..

---

### Post by peav007 on 2006-08-29
does anybody know how i can remove these drivers from within ndiswrapper


cheers john:-k :-k :-k

---

### Post by parliminux on 2006-10-03
you'd type sudo ndiswrapper -l "drivername"

---

