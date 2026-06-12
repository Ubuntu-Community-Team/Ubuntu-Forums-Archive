---
title: "eno1 and &quot;wired connection&quot;"
date: 2020-02-18
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2020-02-18
Hi,
i use KDE on ubuntu 19.10 and in order to view geo-restricted reportages/videos news, i have a VPN provider.
From version 18.x of ubuntu i discovered that i do not ONLY have a "wired connection" (see picture) but also a "eno1".
[[IMG]https://i.ibb.co/Mgr32TL/2020-02-18-network-ocnnection.png[/IMG]]("https://imgbb.com/")
Both have the same IP address, however VPN do not work on eno1 but only with "Wired connection". I do not know why but this is a fact.
Therefore i would like to set my "Wired connection" As default and remove "eno1" from available network interfaces.
I tried to add to kernel boot in grub "net.ifnames= biosdevnames=0" thing but without success as it remove the "Wired connection" AND "eno1" from available network interface (and fall back to eth0)

So what should i do to not be forced each time i want to see reportage geo-restricted to manually connect to "wired connection" ?

thx

---

