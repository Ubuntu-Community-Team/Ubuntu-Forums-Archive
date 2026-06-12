---
title: "Nic replacing"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by lanux on 2007-06-30
Hi !

I am replaced my network interface in my command line system (feisty)
How to set up my new nic (rtl8139) ? It is don't working.
I don't have /etc/iftab...

Thx

---

### Post by p_quarles on 2007-06-30
The E10/100 driver built into the Linux kernel has worked just fine for all of the wired NICs I've used. On the two occasions I had a problem (while trying to repair an older system), I discovered that either the NIC or the PCI bus was just a tiny bit loose. So, if nothing else, you could try making sure everything is secure inside the box.

---

