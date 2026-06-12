---
title: "Can't get IP address with 4306"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by balloniw on 2006-10-31
Hi all. This is my first post so please be kind :).

I have been trying to establish wireless connectivity for a frustrating 2 days with no luck. I believe I am very close, but yet so far.

I have a Dell D600 with the Broadcom 4306 wireless miniPCI card. I am running Dapper. I installed ndiswrapper and followed the steps to install the Windows driver for the 4306 (I have tried a couple of drivers from different sources). I have enabled the eth1 interface via network settings admin tool, and have entered my ESSID and WEP (ASCII) key. Network settings says the interface is active.

The problems start here. iwconfig will not seem to take my ESSID entered in network settings. I can force it in manually using iwconfig at the command line. In my environment the ESSID is not broadcast and has a "*" character in it (not my doing); not sure if this is relevant. The security mode is also set to restricted. Once the ESSID is correct, and the security mode is set to open, the iwconfig output looks good. Even `iwlist eth1 scan` works as expected. Yet, ifconfig still shows that I haven't got an IP address. 

What do I need to do to get dhclient (which I see is running for eth1) to get an address?  Thanks in advance.

Bill

---

