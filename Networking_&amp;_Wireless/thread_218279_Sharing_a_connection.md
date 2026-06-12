---
title: "Sharing a connection"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by Sart on 2006-07-18
The problem is that my girl got a computer herself recently. I use Ubuntu Dapper Drake and she prefers WinXP SP2. I have an internet connection (IP address is assigned by DHCP server of my ISP, but it is always the same) through eth1. I also set up a network between our PCs through  eth0. IPs were assigned manually, mine is 192.168.0.1, her is 192.168.0.2 
I tried several variants of setup, but none worked. I need both PCs to be able to use Internet. What should I do?

---

### Post by monkieie on 2006-07-18
silly question - why do you want them both to share the same connection through each other? Why not simply connect them both via a hub - or even better - a simple ethernet switch? I obviously don't know if you are a dial-up customer or connecting via cable, DSL etc. but (unless it's dial-up) a switch would be the better option. Then you wouldn't need both computers on simultaneously to access the net. :)

---

### Post by az on 2006-07-18
You can either do this:
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28masquerading%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28masquerading%29)

or install firestarter and configure your connections for sharing (masquerading).  You want to share your ethernet connection with hers.

---

### Post by Sart on 2006-07-19
> **monkieie said:**
> silly question - why do you want them both to share the same connection through each other? Why not simply connect them both via a hub - or even better - a simple ethernet switch? I obviously don't know if you are a dial-up customer or connecting via cable, DSL etc. but (unless it's dial-up) a switch would be the better option. Then you wouldn't need both computers on simultaneously to access the net. :)

I use a cable connection. Authorization is by MAC address, so only my box should be connected directly to the wire, otherwise I'll have to go to my provider's office to confirm the MAC change and pay for it.

---

### Post by Sart on 2006-07-19
> **azz said:**
> You can either do this:
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28masquerading%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28masquerading%29)

or install firestarter and configure your connections for sharing (masquerading).  You want to share your ethernet connection with hers.

I tried Firestarter already. No good. Maybe I jus did smth wrong?

---

### Post by monkieie on 2006-07-19
> **Sart said:**
> I use a cable connection. Authorization is by MAC address, so only my box should be connected directly to the wire, otherwise I'll have to go to my provider's office to confirm the MAC change and pay for it.

Which MAC address is registered with your provider? The one of the modem or the one of your pc? To check your address on the computer you cann carry out the following command in the terminal:

under Windows:
arp -a 

under Linux:
arp

The MAC address is stored in the ARP table, which uses the ARP protocol to translate IP addresses in the network.

**For example:**
*192.168.1.1 wants to send information to another computer on the LAN that has an IP of 192.168.1.2* 
192.168.1.1 will then first send out a broadcast to all stations on the LAN asking who has the IP 192.168.1.2. Then the box that has 192.168.1.2 will respond to 192.168.1.1 with it’s MAC address which is cached in 192.168.1.1’s ARP table for later use.

If you are unlucky enough to have had the MAC address from your computer registered with your provider, then you would indeed have to inform them of the change of MAC if you decide to insert a router after the modem. This would be a one-off thing though. Lots of routers even allow you to change the MAC address on the WAN card, you could indeed then reconfigure it to take the "registered" MAC address of your computer. Perhaps it would be worth checking out, depending on how proficient you are.

If you should ever want to change your MAC then it really is very simple (under Linux at least).This would also have the added advantage of preventing spoofing attacks out of the internet:

    ifconfig eth0 down hw ether 00:00:00:00:00:01

    ifconfig eth0 up

These commands would set you eth0 interface to use the MAC 00:00:00:00:00:01. Just insert the NIC you want to set and the MAC address you want to use into the commands above and your done.

---

### Post by Sart on 2006-07-21
Unfortunately, ISP registered my PC's MAC...

---

