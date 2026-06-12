---
title: "Wireless no longer working"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by rcsarver on 2007-06-20
A couple of days ago, my wireless internet stopped working for apparently no reason. I am running gnome ubuntu with the latest kernel on a HP laptop, and it was working fine until a couple of days ago. There is a bug in the new kernel having to do with wireless, but I don't think it is the problem because ubuntu recognizes my wireless - it just doesn't connect to any networks.

I am not using ndiswrapper because I didn't need it before.

I have an ethernet connection that works, and an internal wireless card (prism 2.5 wavelan)

Under network-admin, the settings appear as:

"
Wired connection (wlan0)
Wired connection (eth0)
"

To me, it seems counter-intuitive for the wireless to be called a "wired" connection.

My /etc/iftab/ is as follows:

"
eth0 mac blahblah arp 1
eth1 mac blahblah arp 1
"

I am also wondering whether eth1 should be replaced with wlan0 so it matches network-admin. I tried changing and it didn't seem to help.

My /etc/network/interfaces/ is:

"
auto lo
iface lo net loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
"

I have tried adding an entry for wlan0. Also, do I really need ath0 or eth2? I have tried every combination I could think of playing with those two files and network-admin. I don't know what else to toy with to get this thing working. Any help would be appreciated!

---

### Post by chili555 on 2007-06-20
> do I really need ath0 or eth2?Nope, nor wlan0, unless you have 4-5 wireless cards and need an interface for each.

I think the problem is that too many modules load for Prism 2.5 cards. Amazingly, the one that causes trouble is prism2_<whatever>. Please do ```
lsmod | grep prism
```If you find an entry, let's blacklist it. *sudo gedit /etc/modprobe.d/blacklist* to add an entry:```
blacklist prism2_cs
```Substitute whatever you found for the module name. It may be prism2_pci or otherwise. Reboot and let us know.

---

### Post by rcsarver on 2007-06-20
It worked. Thank you for your time!

---

