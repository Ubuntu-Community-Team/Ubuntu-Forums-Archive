---
title: "Wifi works in Live CD but not on full install"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Rendawg on 2007-06-09
Hey Everyone,

Fairly new to Linux (although I have messed around a bit over the years) and I have an issue I'm hoping someone can help with.  

Loading the live CD on my Toshiba satellite 5200 laptop works great; everything works.  I finally did a full install last night and I can't get the wireless to connect.  It works fine under the live CD (full internet access after I type in the security key) but when I try to connect via the full install it just goes around and around without verifying my login and finally locks my system up.  Wired works fine but no wireless love.

I can see my wireless network and i have a great signal I just can't authenticate to it.  Any ideas?

Thanks,
Rene

Wireless Card: D-link DWL-650 (fully supported)

---

### Post by Rendawg on 2007-06-09
Update....

After doing some more looking around i noticed by using the 'lshw -C network' command (no quotes) in a terminal window (Applications/Accessories/Terminal) that my wireless card (Eth1) was not being recognized.  This is very strange since I had absolutely ZERO problems with the live CD.  Anyway, luckily I had another wireless card around and I popped that into the PCMCIA slot and I had wireless back.  It's another D-LInk card WNA-1330 (on the approved list).  

All is fixed on this end.  Time to start really learning this thing.

Cheers,
Rene

---

