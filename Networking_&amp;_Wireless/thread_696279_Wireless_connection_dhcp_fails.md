---
title: "Wireless connection: dhcp fails"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by bbukh on 2008-02-13
I have a PCI card with rt61 chipset. I have a dual-boot system. The card works perfectly unde Windows. I also run Kubunto 6.0.6 (Dapper).  The card is properly detected and driver is loaded, and I can scan networks, but when I try to connect dhcp fails.

What I tried:
First of all, **wlassistant** shows the list of available networks including the networks I want to connect to. Attempt to connect to any of them results in "connection failed". I tried connecting both to unsecured and secured networks with same result. When I try todo everything through command line, here is what I get:

**sudo iwlist ra0 scan**
gives me a list of all networks in the range, including the networks I want to connect to. After setting parameters with **iwconfig** and running 
**sudo iwconfig ra0**
shows that the the reception is very strong, However, issuing **sudo dhclient ra0** results in time out without any responses received.

I am able to connect to a network through Ethernet cable. I can connect to the wireless networks under Windows on the same machine as well as on the other linux machine.

I also tried installing the latest drivers from RAlink. The symptoms are exactly the same with a different driver. 

I also tried running ubuntu 7.10 live-CD. It exhibits exactly the same symptoms (can scan and see networks, but dhcp fails)

What I should check next?

Thanks in advance for any help,
Boris

---

