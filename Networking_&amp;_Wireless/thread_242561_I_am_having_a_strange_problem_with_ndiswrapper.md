---
title: "I am having a strange problem with ndiswrapper"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by bensexson on 2006-08-23
My wireless is working at home and other WAPs.  The problem is at my university.  They have a broadcast ESSID of IU Wireless with the spaceand no encryption on the wireless (they use a PPTP MS_CHAP VPN).  This worked before I wiped my install during my upgrade from Hoary to Dapper.  With ndiswrapper for my bcm4306 it will not commit an iwconfig eth1 essid "IU Wireless".  It just comes back with an ESSID of any.  If I switch to bcm43xx this will work (I use ndiswrapper because bcm43xx only works at 11Mbps).  If I switch to bcm43xx set the ESSID and then switch back to ndiswrapper it has the correct essid and it all works.  I have a bootup script to set the networking so I would like tofigure this out instead of just doing this manually.  I have workaround but it is clunky.  Has anyone else seen this?  Or any ideas?:confused:

---

