---
title: "AD DNS multiple entries with IP aliases and VMware"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by robwicks on 2007-03-29
I have an Ubuntu 6.10 workstation which uses DHCP. I am also doing some local networking on a hub with another 6.10 laptop. I don't want my IP address to change while I work working connections between the computers, and that has happened before, so I added a eth0:1 entry to /etc/network/interfaces with a private IP which is unused on our entire network. I also use VMWare workstation which is set up using NAT. As a result, my workstation my have 4 different IP addresses, though only one is used to access the Internet. I notice that when I do 'host workstationname', I see all the IP addresses currently on the machine. I can only assume that dhclient or something is updating the Windows Active Directory DNS entries. I do run daap from workstation to another so I can listen to rhythmbox on the laptop streaming from the workstation. Is there any way I can stop the ddns updates on any IPs other than the one on eth0?

---

