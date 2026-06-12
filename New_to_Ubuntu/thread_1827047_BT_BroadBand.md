---
title: "BT BroadBand"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-08-17
I use Ubuntu 11.04 and I have decided to change my ISP to BT broadband.

A friend of my said that there were comparability problems with the BT hub, has any member of this forum had any problems with BT.

---

### Post by Carterclan on 2011-08-17
Hi I don't have BT Broadband myself but I have recently converted a friend of mine from Windows to Ubuntu. He is running 11.04 with a BT Broadband home hub without issue. In fact I've never heard of anyone having compatibility issues with any of the major ISP routers and Ubuntu.
Hope this puts your mind at rest:D

---

### Post by Robert1305 on 2011-08-17
Thanks for the reassurance CC, I don't make the change over to BT until the 1st of Nov, so my mind will not be completely at rest until the 2nd of Nov. :):)

---

### Post by fidelandche on 2011-08-17
Hi,

I have BT Broadband option 3 and I have no problems with it and I am running Ubuntu only. The only issue I have come across is if your hub needs resetting and BT want remote access to your desktop they can't if you only run Ubuntu, but if I can find the IP address for the hub (it is a universal IP address, just different passwords) I will send it to you via PM.

Cheers

---

### Post by SavageWolf on 2011-08-17
You can get to the bthomehub's page thing by going to [http://bthomehub.home](http://bthomehub.home)

I use BT Broadband and it works fine, though now and again the network slows down for no good reason or disconnects...

---

### Post by MG&amp;TL on 2011-08-17
I have  BT hub via in-built wireless (in a laptop) and USB adapter, and they both work fine.

---

### Post by Carterclan on 2011-08-17
> **SavageWolf said:**
> 
I use BT Broadband and it works fine, though now and again the network slows down for no good reason or disconnects...

I think the same can be said of most isp's. They are usually slowing us down on purpose.

---

### Post by CatKiller on 2011-08-17
No problems at all when I set up my mum's. I think your friend was misinformed.

> **fidelandche said:**
> and BT want remote access to your desktop they can't

What the hell? Why would you want them to? Not letting some call-centre monkey have access to your computer is a brilliant reason to use Linux.

---

### Post by haqking on 2011-08-17
none at all, though i always replace BT Hub.

I am using Netgear as the hub itself would not connect at the same speeds my Netgear does.

I have a BT Home HUb v2 and a BT Homehub v3 for sale consequently ;-)

---

### Post by The Cog on 2011-08-17
I've used BT broadband at two different relative's houses, both wired and wireless at both houses. No problems, with several different versions of Ubuntu.

---

### Post by Elfy on 2011-08-17
Using wired here on two machines, the one upstairs had no issue using the wireless when that was the case.

---

### Post by taural.cw on 2011-08-27
There is a slight issue with the HomeHub following a relatively recent update that become an issue if you plan on running a dual boot system:

This issue has been discussed on the BT forum. it seems that the latest firmware upgrade pushed out by BT for the v2 hubs is causing this problem;

The latest firmware version (4.7.5.1.83.3.18) included a fix to ensure disconnected devices are released from the Hubs DHCP table.
As our requirements for the hub don’t specifically support multiple IP hosts with the same MAC address, this specific scenario with dual boot set-ups was not tested for this upgrade.  After your reports on the forum we are now working on a solution, thanks for flagging this to us.
In the meantime we have identified a work around that you can use. The network interface on the Ubuntu operating system needs to be configured to use a fixed IP address. This must be set in the operating system’s network settings and not the Hub’s GUI.


The following is a "how to fix" posted by a user on the BT forum:

I then tried the fixed IP route.  It worked.  To set this:

right click on network manager in the notification area at the top and click on 'Edit Connections'

Click on the Wireless or Wired tab as appropriate, click on the connection you want and click on Edit

Under IPv4 settings click Add to enter this information:

IP Address - 192.168.1.xx (last 2/3 digits any available address on your network)

Subnet Mask 255.255.255.0

Gateway - 192.168.1.254

DNS Server - 192.168.1.254.

Remember to make it available to all users if you have have more than one user on your PC and it will all work fine.


Just something to consider, though the workaround isn't much hassle.

---

