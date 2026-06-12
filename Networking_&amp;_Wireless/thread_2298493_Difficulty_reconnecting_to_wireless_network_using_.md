---
title: "Difficulty reconnecting to wireless network using BCM4312 on HP Mini"
date: 2015-10-11
forum: Networking &amp; Wireless
---

### Post by Graham_Mitchell on 2015-10-11
I'm new to Ubuntu. I've successfully installed 14.04 LTS on a newly acquired HP Mini (N450 Atom 1.6GHz, 2GB RAM). The machine has a Broadcom 4312 card for wireless networking, and I've followed the information at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) in order to get the Broadcom STA driver installed.

Once I have a connection it is stable and works fine. However if I restart the machine, or suspend it, re-connecting seems to be very unreliable. As and when it does reconnect - most of the time it does not - it's unclear as to why the reconnection attempt has been successful where other attempts have failed. I notice that in the system settings, the Network preferences suggest that it is not connected (when it clearly is), which suggests to me that there may be some conflicting drivers at play perhaps.

Pretty much all the information I can find online focusses on getting the drivers installed for this device rather than any problems once the driver is installed.

Any insights into what might be going on here would be greatly appreciated, or pointers as to how I might start to debug the situation.

Thanks
Graham

---

### Post by Graham_Mitchell on 2015-10-12
Looks like the issue was down to the way the network was configured rather than the client or how it was set up. I have a router to connect to the outside world. It was set up as a DHCP server, and it's wireless adapter was turned off. I have a wired connection from the router to an Apple Airport Extreme base station that is set up to provide a wireless network. (This set-up is simply down to the fact that the Apple base station gives me a method to control timed access for my kids where the router does not offer this type of feature). By changing the configuration of these two devices such that the Apple base station is now acting as the DHCP server for the WLAN the problem appears to have been resolved.

---

