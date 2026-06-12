---
title: "Ubuntu 18 cannot connect to the Internet using eth network"
date: 2019-07-12
forum: Networking &amp; Wireless
---

### Post by ryanyan1010 on 2019-07-12
[COLOR=#242729][FONT=Arial]I just installed Ubuntu in an old PC and I installed the Fog Server in it. For some reason, I made a mistake that I enabled DHCP function, and I tried the way from other website to disable it. I did the following commands:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]sudo dpkg --get-selections | grep dhcp
sudo apt-get remove isc-dhcp-client
sudo apt-get remove isc-dhcp-common
sudo apt-get remove isc-dhcp-server[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And when I run the command:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]sudo dpkg --get-selections | grep dhcp
isc-dhcp-client deinstall
isc-dhcp-server deinstall[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And now I cannot connect to the Internet and even there is no connection icon in the menu of the upper right corner. I think remove that dhcp stuff caused this disconnection and wonder if there is any solutions to reinstall it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The Ubuntu cannot connect to the Internet but I got a windows PC here to help[/FONT][/COLOR]

---

### Post by TheFu on 2019-07-12
In general, it is best to disable a service, check out how things work, wait a week, see if there are repercussions, then consider removing the packages.
BTW, if you setup a static IP on a specific interface, that should disable the same interface being used for DHCP, but in 18.04 networking got massively changed, so I can't be positive.

If you just installed the OS, I would just reinstall.  It only takes 10 minutes.

Also, it would be helpful if you specified which version of Ubuntu you are working with - there are about 6 popular versions of 18.04 and we'd rather not have to assume any specific version.

Sometime in 2015, the network device names changed, so it is very possible that no eth0 or eth-anything exists.  On one of my systems, the NIC is enp3s0.   Basically, the driver decides the name since 2015.

---

