---
title: "MAC Address problems"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by MrGrey1 on 2007-04-11
6.1
Issue: ifconfig displays a MAC address of 00:00:XX:XX:XX:XX for eth0. 
Wake on LAN _WORKS_ with a mac address that is identical except for a 4: 00:40:XX:XX:XX:XX
Question: How do I determine which is the correct MAC and where is it being changed?

I have checked /etc/network/interfaces and there is nothing unusual there, ie no spoofing setup. Is there any other location that this extra 4 could be getting added/removed from? 
This is a real doozy. I need to get both WOL and the ifconfig displaying/working on the same MAC as my router has to be configured with a static ARP table for wake on Internet to work. If I put the MAC address without the 4 into the ARP table then wake on internet doesn't work. If I put the MAC address with the 4 in the ARP table then it kills the  network connection as there is a conflict between the arp table and the ifconfig file. (spoofing the address with an extra 4 in ifconfig also doesn't seem to work)

---

### Post by Iowa Dave on 2007-04-11
What's the actual MAC address of the network interface card?

---

### Post by MrGrey1 on 2007-04-11
> **Iowa Dave said:**
> What's the actual MAC address of the network interface card?

Sorry I'm a little reluctant to post my MAC address on the internet. Why do you ask?

---

### Post by Iowa Dave on 2007-04-12
No need for the information here, so please don't post it.

My thought was to suggest consistency between the configuration information and the actual device.

But hey, you probably knew that already.

Good luck.

---

