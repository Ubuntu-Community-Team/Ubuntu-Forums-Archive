---
title: "WiFi Driver Bug on Hardy"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by balagosa on 2008-05-14
ok, here is the deal.

on Gutsy 7.10, i am 100% sure that my Wireless Card was a certain Atheros AR5006. But during 8.04, it changed it's name to AR242x. as testified by
"lspci"
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

AND
"lshw -C network"
```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

read a bunch of forums, and this is what i dished out. [Forum Source]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/205025")

Take note of what **lod** said. He is having the same problem as me.

Also, My Network Admin has same laptop as mine and he runs Fedora 8. i did lspci on Fedora 8, and what do you know. Atheros AR5006 popped out. so yeah, can someone please second this? for people who have the same situation as me?

and this is probably why when i loaded/reconfigured my WiFi, things didnt work out. because after all those work, my WiFi is still broken ---> ***-network UNCLAIMED** meaning not configured/installed

---

### Post by balagosa on 2008-05-14
now i know why. lspci posted the Chipset. 

[Proof 1]("http://www.atheros.cz/")

[Proof 2]("http://madwifi.org/wiki/Compatibility/Atheros")

Look at 5007EG and 5006EG/5006EGS, Chipset: 2425, and 2423, respectively. 

problem is, why the "x"? so it seems i was on the right path on loading a 5007EG WiFi driver huh? maybe i just missed something resulting to an unsatisfied WiFi connectivity.

---

