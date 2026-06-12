---
title: "Cant figure it out"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by tagh2000 on 2007-04-27
I have a HP ze5385us notebook with a LAN-Express IEEE 802.11 PCI Adapter. Everything works except wireless internet. I have tried to install the ndiswrapper, which worked, but when installing ndisgtk it gives an error message "Error: Dependency is not satisfiable: ndiswrapper-utils". I would like to get this working and connect to the internet. I have tried to use the many how to's and forms posts to solve this issue but I have had no luck. I am a beginner when it comes to linux so any help would be great.

---

### Post by dbott67 on 2007-04-27
Do you have a wired connection that works?  If so, you'll need to get online & run the following command:
```
sudo apt-get install ndiswrapper-utils
```If you don't have a wired connection, then you'll need to download the package to USB drive or some other media from here:

[http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

A search for 'ndiwrapper-utils' (all distributions) returns this [page]("http://packages.ubuntulinux.org/cgi-bin/search_packages.pl?keywords=ndiswrapper-utils&searchon=names&subword=1&version=all&release=all").  Download the appropriate version for your distro & architecture, save it to USB and plug it into your Ubuntu machine.

-Dave

---

