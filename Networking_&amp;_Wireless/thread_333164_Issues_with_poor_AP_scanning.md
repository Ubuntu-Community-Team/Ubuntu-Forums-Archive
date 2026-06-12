---
title: "Issues with poor AP scanning"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by lierodeath on 2007-01-07
Hey there.

I am trying to connect to my wireless network. I am using a Belkin F5D7050 USB adaptor, which is running with the rt73 driver that comes with Edgy.

When I had the computer/wireless card in the same room as the scanner, Ubuntu picked up my AP fine - I had an internet connection, no problems.

When I use the same Wireless adaptor with Windows or MacOSX in my office - they both pick up the AP fine, albeit with not more than 70% signal strength.

However, when scanning for networks in Ubuntu, using "sudo iwlist wlan0 scan", I get nothing. This is with all the relevant hardware in *exactly* the same place as when scanning in Windows. If I drag the router out into the hall and open all the connecting doors, I pick up the AP intermittently in Ubuntu, and get a strong connection in Windows and OSX.

Essentially, Ubuntu seems to be scanning very, very poorly, and not seeing networks unless they are almost on top of it.

I have tried running "iwconfig wlan0 sens", but it tells me my hardware/driver does not support changes to scan sensitivity.

Does anyone know how I might increase my scanning sensitivity, or somehow persuade Ubuntu to see my AP? There is, unfortunately, no question of moving the hardware.

---

