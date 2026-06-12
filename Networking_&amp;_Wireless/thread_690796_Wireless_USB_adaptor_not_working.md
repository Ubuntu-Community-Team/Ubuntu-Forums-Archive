---
title: "Wireless USB adaptor not working"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by LanceMillar on 2008-02-07
I have a SMC easyconnect g wireles usb adapter and it is not recognised by abuntu. There web page doesn't even have a linux driver for it.Please help.:(

---

### Post by bwhite82 on 2008-02-07
With the device plugged in, please post the output of:

> lsusb This is to determine the device's chipset.

---

### Post by jwmcgee1 on 2008-02-07
I am having the same problem with a Netgear adapter:

Bus 005 Device 004: ID 0846:9010 NetGear, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

---

### Post by DataKnutten on 2008-04-30
> **jwmcgee1 said:**
> I am having the same problem with a Netgear adapter:

Bus 005 Device 004: ID 0846:9010 NetGear, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

This device is the Netgear RangeMax Dual Band Wireless-N USB Adapter WNDA3100.
I'm thinking of buying this adapter but I cannot find anything about drivers for Linux.
I found this:
[http://listing.driveragent.com/usb/0846/9010](http://listing.driveragent.com/usb/0846/9010)
where it says its based on a Atheros chipset.
The INF-file [http://driveragent.com/archive/15863/2-1-1](http://driveragent.com/archive/15863/2-1-1) might give some hints too.

You might try help here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

