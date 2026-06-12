---
title: "IPv6 configured but not working on Ubuntu Server"
date: 2021-07-01
forum: Networking &amp; Wireless
---

### Post by cruetz on 2021-07-01
Hey everyone,

I've been tearing out my hair with this problem on and off for months. I have multiple IPv6 enabled machines on my network and all function flawlessly except the Ubuntu Server machine. It seems to be configuring itself properly, has addresses and routing tables that look proper, but it cannot actually communicate using IPv6 at all. Also when it loses its DHCPv6 lease it won't reconfigure automatically and a reboot is necessary for it to refresh. It seems like as soon as things hit the gateway, it stops. I've checked over the gateway settings multiple times and nothing seems to be out of place. This gateway configuration is also working for all other IPv6 enabled devices on my network, including a Ubuntu Server VM with bridged networking. 

Here's what I know:

Machine A: Ubuntu Server 20.04.2
Machine B: Windows 10
Gateway: Ubiquiti Dream Machine Pro

Machine A can ping -6 the gateway
Machine A CANNOT resolve AAAA google.com (but will through IPv4)
Machine A CANNOT ping -6 google.com as it won't resolve
Machine A CANNOT ping -6 the google.com resolved address aquired through IPv4
Machine A can ping -6 itself
Machine A CANNOT ping -6 Machine B

Machine B can ping the gateway
Machine B can resolve AAAA google.com
Machine B can ping google.com (resolves to IPv6 address)
Machine B can ping itself
Machine B CANNOT ping Machine A

Anybody know what's going on?

I've even blown everything away and done a fresh install of the OS but the problem still remains. I've also replaced the motherboard with the onboard network and the problem still remains.

---

