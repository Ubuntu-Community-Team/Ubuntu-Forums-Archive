---
title: "aircrack and rtl8185 question"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by krumble on 2007-12-31
Ok I have a few questions here and I will try to be as specific as I can with them.
First of all I am using the RTL8185 Chipset in my Gateway laptop. I am using Ubuntu Edgy by the way.
1. I would like to use aircrack-ng but I don't know if I need to compile the driver first the instructions kind of lost me.
2. If I do need to compile the driver, which one should I use?  I've seen posts about the [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) driver, but I went to the realtek website and it seem that they also have a driver for the RTL8185 card.  Should I use the opensource driver or the one from Realtek?

---

### Post by Junglizer on 2008-01-03
I would recommend the open source driver as the manufactures drivers usually don't allow the card to be dropped into monitor mode (not needed specifically for the aircrack-ng program, but in order to use the rest of the tools in the suite your card must be able to be put into "RF Mon Mode").

---

