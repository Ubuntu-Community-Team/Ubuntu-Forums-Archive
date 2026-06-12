---
title: "Hardy Heron, system lockups"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Guesser on 2008-05-05
I have installed Hardy on my laptop, and I am getting random system lockups, at first it seemed like it could be overheating, but it also seems to match the symptoms of bug #216124 ([https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/216124](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/216124))
so I think it could well be related to the networking applet
the system doesn't lock immediately after connecting, but after the system has been connected for a while it completely freezes.

my system is an intel c2d, and the wireless adapter uses the rt8187 chipset. I am using the windows drivers with ndiswrapper, as the ubuntu drivers for the wireless seem not to work properly, the wireless works, but has a much reduced range, and disconnects a lot :(

the crashes occur before installing anything except ndiswrapper on a fresh system. the hardware and drivers worked in this configuration in Gutsy

---

