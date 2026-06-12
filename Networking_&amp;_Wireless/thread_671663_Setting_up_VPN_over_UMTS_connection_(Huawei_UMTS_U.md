---
title: "Setting up VPN over UMTS connection (Huawei UMTS USB modem)"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by MMSpeer on 2008-01-18
Hi there,

I have succesfully installed an Internet connection using the Huawei UMTS USB modem. Unfortunately this connection cannot be set up using the NetworkManager (NM), therefore I used WVDial (using Webmin). Although not NM, it works fine. But... in order for me to be able to connect to my work LAN, I need a VPN connection. And I have NOT been able to establish this VPN over my Huawei UMTS USB modem. If I could use NM it wouldn't be a problem, however as mentioned my Huawei UMTS USB modem cannot be connected using NM (at least I do not know how). 

I have tried to ways: pptpconfig and PPTP VPN Client (PPPd version 2.4.4) under Webmin. I have succeeded to get connections with both solutions, however pptpconfig ends with 'Cannot determine ethernet address for proxy ARP' and PPTP VPN Client seems to make the right connection, but does not let me connect to the remote server.

I have browsed over the Net and Forums for three nights now, discovered quite some related topics, however neither of them solved mine.

I am quite new to Linux, however I am determined to completely get away from MS. But being able to do so, I definitively need VPN access using my UMTS modem. So I hope somebody can help me try to find a solution for my problem.
 
I am using Ubunty Gutsy Gibbon (7.10) on a Dell Lattitude D510.

Thnx for your help 
M

---

### Post by Orestez on 2008-04-04
Sry for bumping, but exactly this would solve a problem of mine as well me thinks.

---

