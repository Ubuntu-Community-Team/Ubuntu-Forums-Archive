---
title: "create torrents with qbittorrent and a NAS"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by Ubi_one_2014 on 2014-01-26
Hello

Current configuration:
ubuntu 13.10 64 bits with latest qbittorrent, and latest updates
Qnap TS-119 NAS with 1 TB HD and transmissionbt 2.82 as torrent server

qnap got found under: Dolphin>network>sambanetwork>workgroup>NAS
so i can browse over the nas using dolphin.

under windows, i was able to create torrents by:
Qbittorrent>Tools>torrent creator>Add Map . followed by easily browsing to the nas, ans select the maps

under linux, i can not do this. I can select the map, and then nothing happends? The field remains blank.

How can i solve this?

---

### Post by Ubi_one_2014 on 2014-01-26
1 step further :D

1- install cifs-utils
2- sudo su - [enter]
3- mkdir /mnt/NAS
4- mount -t cifs -o username=NAS-USERNAME,password=PASSWORD //NAS_IP/DIRECTORY /mnt/NAS

example
mount -t cifs -o username=ubuntu,password=mysecretpass //192.168.34.12/MP3 /mnt/NAS

qbittorrent now responds with the full path of the directory that i want to created for torrent:D

figuring out how to do this upon reboot
any input on this  is welcome

---

