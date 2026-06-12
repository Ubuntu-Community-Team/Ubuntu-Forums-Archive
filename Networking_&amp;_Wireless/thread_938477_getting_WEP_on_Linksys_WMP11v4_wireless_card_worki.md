---
title: "getting WEP on Linksys WMP11v4 wireless card working"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by sea_monkey987 on 2008-10-04
hey guys.  i believe the title says it all.  i do have the card partially working under ndiswrapper.  i used the ndisgtk package to install ndiswrapper and just used the gui to install my card using LSIPNDS.inf file packaged with windows drivers.  it works as long as i'm connecting to a non-encrypted access point.

I found this thread: [http://ubuntuforums.org/showthread.php?t=7319&page=1]("http://ubuntuforums.org/showthread.php?t=7319&page=1").  as i understand it from here no one is able to use wep.  My question is does anyone know how to get WEP to work with this card?  i don't care which drivers i use.  I was reading something about someone using the b43 drivers and someone else using hostap drivers (but they were dead threads so i didn't know whether it worked) so I would be willing to use these drivers if they work.

lshw -C network:
```

  *-network:0             
       description: Wireless interface
       product: WMP11v4 802.11b PCI card
       vendor: Linksys, A Division of Cisco Systems
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 00
       serial: 00:13:10:28:b8:8d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsipnds driverversion=1.53+Linksys,07/09/2003,3.01.7.2 latency=64 maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```

---

### Post by sea_monkey987 on 2008-10-05
bump?

---

### Post by sea_monkey987 on 2008-10-09
anyone?

---

### Post by sea_monkey987 on 2008-10-18
just checking if anyone new might have an answer.  bump.

---

