---
title: "NetworkManager works for WEP, not for unsecured"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by Vaz on 2006-11-21
Hi.  I'm having a problem with network-manager being unable to connect to any unsecured wireless networks.  It connects to WEP-enabled networks just fine.

I'm running Dapper on an Acer Aspire 5002.  My network card:

```
vaz@null:~$ lspci | grep -i network
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I followed a tutorial on here a while back to get things set up, but I can't seem to find it now for reference.  The driver that came with my laptop didn't work, so I downloaded one mentioned in the tutorial and it works fine (mostly).  If I disable network-manager and set up my network manually (System->Admin->Networking), it'll connect to anything just fine, and with network-manager it connects to my home WEP-encrypted network fine.  But anytime I try to connect to an unsecured network with network-manager it just hangs trying to connect.

I'm using ndiswrapper of course for a driver:

```
vaz@null:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

Anyone have any ideas or a similar problem?  Let me know if there's anything else I can include to clarify things, unfortunately I've just been settling for the way things are for a while now and can't remember exactly how I set it up.

---

### Post by NetworkGuy on 2006-11-23
There is a bug in launchpad reporting this problem with Network Manager.

---

### Post by Vaz on 2006-11-23
Thanks.  Someone posted a workaround in the comments.  When I get a chance to try it out I will, and I'll post details on how it goes.

---

