---
title: "lxdbr0 and wlan0 hotspot with the same DHCP Server"
date: 2020-04-17
forum: Networking &amp; Wireless
---

### Post by andrew139 on 2020-04-17
Hello everyone,
In my Raspberry (ubuntu server 18.04) I have configured a Wifi Hotspot, which provides network access to computers and cell phones at home. I have also configured LXD with a Btrfs Raid1 on two USB Drives. Containers are located in that Raid1. All good up to this point.

What I am trying to configure now is that the lxdbr0 bridge and the wlan0 interface have the same DHCP Server, in order to have both the containers and the rest of the home computers on the same subnet. Is this possible? How can I do it?

I inserted an image with the network diagram as currently.

[ATTACH=CONFIG]285546[/ATTACH]

---

