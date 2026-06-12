---
title: "netplan: How to connect to a different network?"
date: 2020-05-16
forum: Networking &amp; Wireless
---

### Post by ravijoshi2002 on 2020-05-16
If a netplan config file has more than one access point listed, and computer is currently connected to a network, is there a way to disconnect from current AP and connect to a different point? [using networkd].
This is easily possible in nmcli or wpa_cli if using networkmanager or wpa supplicant respectively, but there appears to be no way if using netplan. Changing AP is possible only if you edit yaml config file, change the order of networks listed and apply modified network plan.
Can someone please point if is a better way?

---

### Post by TheFu on 2020-05-17
I use wicd to manage wifi connections. I suppose nmcli could be used, just always purge network-manager stuff from all my systems after being frustrated with very early versions of those tools.

I use netplan to manage static, wired, ethernet connections on systems with netplan and not ifupdown.

Better way?  I wouldn't know.  Just sharing what I do that doesn't lead to surprises. Your setup might not work in the same way as mine.

---

