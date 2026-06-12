---
title: "Install Remote Printer over WIFI on Netgear 606"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by petersra on 2007-02-24
Hi,

I have a HP Deskjet 5150 printer USB connected to a Netgear 606 Printserver.  I print via a WINXP LAN system and a WINXP wireless thinkpad t60 laptop.  

Now, I am trying to set up the printer in my new KUBUNTU thinkpad (T23) with a WPC54G v3 4318 WIFI card.  Got the WIFI card working after a lot of trial and effort.  However, when I try to install a printer, the test print will not work.  he steps I followed were.

select networked printer
IP address set
Port 515
can't specify a queue (L1)

The print-state-message I get is socket failed.

Ideas?
Rob

---

### Post by tgalati4 on 2007-02-24
In firefox:

localhost:631

Ubuntu uses the CUPS printing system.  Master it and all of your printing problems go away.

Search CUPS in the forums as there are several decent tutorials.

Wireless printing can be tricky because it is treated as "outside the network" so you may have to set up some special access and priviledges.  HP printers are well-supported in Linux.

---

### Post by petersra on 2007-02-25
Thanks.  Got it working with this configuration:
lpd://ipadress/L1:

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by tgalati4 on 2007-02-25
Great news!  Now share your CUPS prowess with others.

---

