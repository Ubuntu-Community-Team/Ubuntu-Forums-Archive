---
title: "No network after updates"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by larrys on 2008-01-28
I am running VMware Workstation 6.0.2 and have installed Ubuntu linux 7.1 as guest. Everything was fine until I installed all the suggested updates yesterday and since then I no longer have network connectivity. I am using Bridged mode in VMware and have tried Roaming mode and DHCM in Ubuntu without success. I  have disabled ipv6 as suggested in a thread (alias net-pf-10 off ip). The host (XP box) has a direct internet ethernet connection with DHCP and it works fine.

I looked at "network connections " on the host and it only sees VMnet1 and VMnet8. 

Running ifconfig on the guest gives only Local Loopback. 
I tried running "ifup eth0" on the guest and it said "ignoring unknown interface eth-0=eth0".

I guess the problem is that the eth0 is not being installed in the host.

Any suggestions would be greatly appreciated.

Larry

---

### Post by tra4d on 2008-02-01
I am having the same problem.  I did some updates yesterday, rebooted and now I have no network connection.  Unlike larrys my host (Ubuntu 7.10) does not have any network connection either.

Anybody else experiencing network problems after updates?

---

