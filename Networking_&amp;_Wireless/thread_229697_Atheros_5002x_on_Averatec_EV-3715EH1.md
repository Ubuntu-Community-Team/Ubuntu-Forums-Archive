---
title: "Atheros 5002x on Averatec EV-3715EH1"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by Cobalt Infinity on 2006-08-04
Good Afternoon all.  First off, everyone here helps contribute to a pretty awesome experience to a linux newbie.  I have always been a windows guy and even more recently apple.  I am extremely literate when it comes to all things hardware and windows but Linux is not something I am all that familiar with.  I purchased an Atheros 5002x Mini-Pci card from the HOPE conference and installed it into my laptop with an external 7db antenna.  Everything works in window but Ubuntu is not cooperating with the wireless.  Does anyone have any experience getting this particular card to work withOUT the ndiswrapper?  I really dont want to use ndis unless absolutely necessary.  Thank you all for your help!

Cobalt

---

### Post by tturrisi on 2006-08-05
Use Synaptic to install the linux-restricteed-modules for your kernel.  You do NOT want to use ndiswrapper for atheros chipset cards.

---

