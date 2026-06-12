---
title: "How to change wireless card drivers for packet injecting?"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by magnav0x on 2006-10-03
Ok, I'm trying to get packet injecting working under Ubuntu with my  Senao NL-2511CD Plust EXT2 PCMCIA card (Prism2.5).  I've had it working under Backtrack in the past, so I know the card is fine.  

Ubuntu detects the card when I insert it and assigns it to ETH2.  However when I run airmon to turn on monitoring mode it shows HermesI for the chipset and Orinoco for the driver.  Why does this show up as a HermesI chipset and how can I switch from the Orinoco drivers to either HostAP or WlanNG?

Also, what is the easiest way of verifying if packet injecting is actually enabled?

---

### Post by magnav0x on 2006-10-04
I find it hard to believe no one on these forums knows how to change drivers in linux.  Anybody?

I've tryed blacklisting the orinoco drivers as well, but when I stype 'lspci' I still see the orinoco and orinoco_cs modules listed.

---

### Post by tturrisi on 2006-10-04
Ubuntu use orinoco_15x & I believe that version broke monitor mode.  You may need to use an older version.

---

### Post by magnav0x on 2006-10-04
I don't want to use the orinoco modules at all

---

### Post by tturrisi on 2006-10-04
according to the aircrack web site to use w/ prism chipsets the drivers need to be patched.  It's possible that Backtrack has already patched drivers.
[http://www.aircrack-ng.org/doku.php?id=compatibility&DokuWiki=52d313af498ca22feb8880482fc78292](http://www.aircrack-ng.org/doku.php?id=compatibility&DokuWiki=52d313af498ca22feb8880482fc78292)

also see this:
[http://www.ubuntuforums.org/showthread.php?t=221144](http://www.ubuntuforums.org/showthread.php?t=221144)

---

