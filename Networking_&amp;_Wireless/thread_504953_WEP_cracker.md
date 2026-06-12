---
title: "WEP cracker"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Morhas on 2007-07-19
Is there any WEP cracker that I can use that will work with ndiswrapper drivers? I have a broadcom wireless card in my laptop, and I can't seem to find anything so far.

Any help would be appreciated.

---

### Post by jml on 2007-07-19
Most sniffing software requires that the wireless card be placed into a passive monitor mode.  I do not believe that the Broadcom card can go into monitor mode.  I use a card with the Atheros chipset for this purpose.

On another note, an easier way to get the software you are interested in is to download the Backtrack live CD.  Here is their web site:

[http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)

This live CD has a complete suite of network tools collected into one CD. Check it out.

Joe

---

### Post by tturrisi on 2007-07-19
Ndiswrapper drivers cannot be put into monitor mode.  The possible exception is using a Windows driver that has monitor mode capability, such as the Airpeak drivers or Comm View drivers for specific chipsets.  (afaik there are none for Broadcom chipsets)

However, the linux broadcom driver works well and also supports monitor mode.  It baffles me why so many people use ndiswrapper for broadcom devices when native support is built into tghe kernel for that chipset.

---

