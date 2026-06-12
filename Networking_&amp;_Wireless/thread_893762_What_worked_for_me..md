---
title: "What worked for me."
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by wg5o on 2008-08-18
After struggling all summer, I have wireless working.  My primary problem turned out to be 64-bit Ubuntu.  Ndiswrapper wouldn't install a 32-bit driver, and when I did find a 64-bit driver, the module wouldn't load.  A member of the local Linux group suggested that I try the 32-bit version of Umbutu.  I wasn't aware that I had that choice, with my 64-bit system, but I learned that I did and finally downloaded the 32-bit version of Ubuntu 8.04.1.  Here is what worked:

1. I made a clean, new installation of 8.04.
2.  I used Synaptic Package Manager to install the three components of the GUI ndiswrapper, then I used it to install the Win XP .ini file from the card's CD.
3. "ndiswrapper -l" showed that the driver was installed and the hardware was present.
4.  "modprobe ndiswrapper" loaded the module.
5.  Then I tried "sudo lspci -nn," "sudo iwconfig," and "sudo ifconfig" to check.  They all indicated success.
6.  I tried to connect and was reminded to supply the network password.
7.  I tried Firefox.  Success!  For the record, this was with an Encore ENLWI-G2 PCI card, Realtek RTL-8185 chip set (rev 20).

Actually, once I got it right, it was easy.

Andy Pickens
San Antonio, Texas
"Sometimes the magic works, sometimes it doesn't."

---

