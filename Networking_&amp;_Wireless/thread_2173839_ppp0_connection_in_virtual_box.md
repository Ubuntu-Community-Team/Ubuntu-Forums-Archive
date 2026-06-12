---
title: "ppp0 connection in virtual box"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by prabhanjan2 on 2013-09-11
Hi all..

I am newer to linux.

I have installed ubuntu as the base operating system.
and debian as guest operating system in virtual box.

Issue is : I connected with internet through Reliance net connect dongle .This ISP provide IP as PPP0 interface.
through this IP i'm not able connect internet to my guest os (debian) in Virtual box.
tried both NAT and Bridge mode  No result.

Thanks

---

### Post by SeijiSensei on 2013-09-11
The ppp0 interface connects the Ubuntu host to the Internet.  If you want to see the guest, you need to communicate over the private network VirtualBox sets up between the host and guest.  On both machines, you should see a vboxnet interface with an address beginning with 10.  You should be able to ping each end of the connection and connect to any services you might have activated like openssh-server.

You cannot use bridge mode because that would require you getting multiple IP addresses from your ISP.  You're limited to NAT.  When the host is connected via PPP, you should be able to open a browser in the guest and surf from it.  If the guest runs only in text-mode, like Ubuntu server does by default, then you'll need to use the elinks browser.

---

