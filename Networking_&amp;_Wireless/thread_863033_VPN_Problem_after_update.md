---
title: "VPN Problem after update"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Kabir on 2008-07-18
Hello,

After an update I've made on 17.07.08, my vpn (cisco) connection does not work.
The updated packages are:
linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb
linux-headers-2.6.24-19-generic_2.6.24-19.36_i386.deb
linux-headers-2.6.24-19_2.6.24-19.36_all.deb

I'm using a Wireless connection and vpn session (cisco vpn client or vpnc) over it.
I have no problem connecting with the wireless network, but after establishing the vpn session I do not have any connectivity with the outside network.
Right now I'm with  2.6.24-18-generic and the same network configuration works perfect.
The connection manager is Network Manager. The wireless module I'm using is ath_pci.

Anybody experiencing the same problem?

---

### Post by ilrudie on 2008-07-18
I always have that problem when I get kernel updates.  I have to use the cisco version of the software which needs to be reinstalled every time you get a new kernel.  Annoying.

I think the problem is essentially the same as people with proprietary nvidia drivers.  It needs a kernel module that isn't maintained by the Linux Kernel folks so it needs to be installed every time you get a new kernel.  There was a good article on the need for community maintained drivers a while back.  If you are interested I can try to dig it up again.  Just let me know.

---

### Post by pmarkov on 2008-07-19
I have the same issue - after update a couple of days ago VPNC stopped working... Or actually it's not completely broken but it began to act confusing - after reboot the first attempt to establish VPN to some site is successfull but it refuses to connect to other VPN site - the funny thing is that it's possible to reconnect to the first VPN site. When I reboot it allows me to connect to other VPN site but again this will be the only possible site until next reboot :-) Any ideas on this strange behaviour?

---

