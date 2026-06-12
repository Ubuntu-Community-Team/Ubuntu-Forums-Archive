---
title: "Holy God!  Now my wireless has disappeared..."
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by finalrequiem on 2008-09-27
I have been having trouble with my wired connection (see thread: Strange Problem...).  I installed Virtual Box and a bunch of updates, restarted and now I have no wireless either.  I am on another computer so I will have to type out the results of "lshw -C network" and "ifconfig"

*-network UNCLAIMED
  desc: Ethernet cont.
  prod: 82566DC Gigabit Net Connection
  vend: intel
  phys: 19
  bus : pci@0000:00:19.0
  vers: 03
  widt: 32 bits
  clck: 33MHz
  capb: cap_list 
  cnfg: latency=0
*-network UNCLAIMED
  desc: Network cont.
  prod: PRO/Wireless 4965 AG or AGN network conn
  vend: intel
  phys: 0
  bus : pci@0000:00:03.0
  vers: 61
  widt: 64 bits
  clck: 33MHz
  capb: bus_master cap_list  
  cnfg: latency=0
------------------------------------------------------

lo     link encap:Local loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 metric:1
       RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
       TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:88900 (86.8 KB)  TX bytes:88900 (86.8 KB)


ThinkPad T61p,  I have no ethernet cord plugged in when I ran these commands.

---

### Post by finalrequiem on 2008-09-27
Wireless seems to work with live cd...

---

### Post by finalrequiem on 2008-09-27
Anyone?  I'm quite confused...

---

