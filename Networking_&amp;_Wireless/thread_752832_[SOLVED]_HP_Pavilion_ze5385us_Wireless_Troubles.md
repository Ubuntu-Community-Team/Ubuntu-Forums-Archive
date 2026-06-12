---
title: "[SOLVED] HP Pavilion ze5385us Wireless Troubles"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by ritdude on 2008-04-12
I have a HP Pavilion ze5385us (ze5300 series).  I have been trying to get the internal wireless to work on it, but I have been having trouble.  I currently have ndiswrapper installed and working (I am currently using an external radio which I was able to successfully install the drivers for).  I have tried a bunch of things to try and get it to work.  I went to the Windows partition (which the internal currently works on) and looked at the driver details.  I have also been searching forums for days now, but to no avail.

I run 7.10 Gutsy.

Network Controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

greg@myspecialplace:~/Desktop/hostapd-0.5.10$ ndiswrapper -l
bcmwl5 : driver installed
netfa312 : driver installed
        device (100B:0020) present (alternate driver: natsemi)
netmw245 : driver installed
        device (13B1:0029) present
oem5 : driver installed
        device (1260:3873) present (alternate driver: hostap_pci)
oem7 : driver installed
        device (1260:3873) present (alternate driver: hostap_pci)
prismnic : driver installed
        device (1260:3873) present (alternate driver: hostap_pci)

Any help would be appricated, im getting frusterated.

---

### Post by ritdude on 2008-04-13
Updated to Hardy Heron (out of the box configuration for this chipset).  I would suggest waiting to upgrade until a stable release is out if you are looking to solve the same problem.  I had to fresh install Hardy cause collectd failed on me.

---

