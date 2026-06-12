---
title: "Windows traffic slowed when going through a Ubuntu 12.10 gateway/router"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by lostnode on 2014-09-22
Hellu Ubuntu Community,

I have been using Ubuntu 12.10 for the last 2 years as a gateway/router for my workplace.  We have 2 networks going into it, and one internet connection, so 3 nics in total.

Recently we started to experience some problems with our network, the traffice seems really slow.  I do a few speed tests from the server, and I get the usual speeds, however I run a speed test from inside and although I get my download speeds, my upload speeds go no where, often returning an error that the upload failed.  Running a text based version, I get that it could no longer reach the server in question.

Here is what I have done so far.
1. Tested internet connection directly (laptop to modem) No issue
2. Tested Server to Internet *(server to modem) no issue
3. Windows from inside the server to outside - Upload failure (on both networks)
    Disabled all firewalls - Same issue

Here is the kicker... if I run a live CD on Linux on any of the internal hardware, No issue.  I run speed test from a linux system, full up and down.  Windows on same system, Full down, little to no up.  If it does manage to get through, I get anywhere from 0.1Mb/s to 0.5Mb/s up instead of the usual 3Mb/s.  So why is Unbuntu rejecting Windows?  

I have disabled IPv6 in the past as it seemed to kick off one of the networks IPv4 address, so I know thats not the issue.  It just strikes me that Linux has absolutly no issue.
I have also updated the system in an attempt to see if that would fix the issue, no resolve.

Anyone have any ideas?

---

### Post by tgalati4 on 2014-09-22
Use *etherape* to visualize your network.  Use *tcpdump* to capture packets from the bad actors.  You will need to share some data because network troubleshooting is difficult without real data.

If you have some process on the Windows machines that is changing the MAC address of the Windows machines, then the return packets will get lost.  The IPV6 issue is probably the settings on a router that require it for address translation.  You can probably turn that off and make the network visible again when using IPV4 only.

I presume that this setup worked flawlessly for 2 years, then all of a sudden, it started acting strange.

Examine UPnP broadcasts from the Windows machines, because can cause some routers to slow down or create a network storm.

---

