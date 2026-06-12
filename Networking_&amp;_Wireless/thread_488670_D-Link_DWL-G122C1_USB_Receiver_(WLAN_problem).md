---
title: "D-Link DWL-G122/C1 USB Receiver (WLAN problem)"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by Xs1t0ry on 2007-06-30
Xubuntu 7.04 (Stock)
D-Link DWL-G122/C1 USB receiving signal from D-Link 524-L Wireless Router

lsusb
```
eric@eric-desktop:~$ lsusb
Bus 005 Device 003: ID 07d1:3c03 D-Link System 
Bus 005 Device 002: ID 058f:9380 Alcor Micro Corp. Flash drive
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00d1 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000 
```

I have extracted ndiswrapper to ~/ndiswrapper/ndiswrapper-1.74 but the install failed. Currently, at startup, Xubuntu gets stuck indefinitely at the loading bar while attempting to 'Configure Network Interface.' Advice, please?

---

### Post by tprzepiorka on 2007-07-13
Hey,
i have the same adapter, but I found that the NDISwrapper drivers don't work that well. I then found this website:[URL="http://linux-wless.passys.nl/query_part.php?brandname=D-Link"]
 http://linux-wless.passys.nl/query_part.php?brandname=D-Link[/URL]

It links to two different sites ([this]("http://web.ralinktech.com/ralink/Home/Support/Linux.html") and [this]("http://rt2x00.serialmonkey.com/")) The one from Serial Monkey was the only one that worked, so you can try that. I hope it helps. I have also included the driver files in the post for you to download. My first "helping" post, hope it was ok :D

---

