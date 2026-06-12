---
title: "ndiswrapper and belkin F5D7000"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by notnic on 2008-07-02
Hi Everyone.
Im trying to get started at using ubuntu and need some help with getting my wireless card working. I am using ubuntu studio, Windows wireless Drivers (the frontend for ndiswrapper) and the belkin F5D7000.

I have managed to get the .inf loaded onto ndis wrapper with all the other files that are in the folder. This is confirmed when I check using the terminal too. It also detects the driver is working and that the hardware is connected.

My problem is that when i check network tools, all I have is `lo` and `eth0` (my wired NIC). In `network` the wireless option is either not there or states `the network interface is not connected`.

I know it must be something simple but I cant work it out from the other threads.

Thanks in advance!

---

### Post by notnic on 2008-07-03
Found the solution:

sudo ifconfig wlan1 up

(The wlan1 bit might be wlan0 or wifi. I found out by opening up KwifiManger and the interface name was displayed at the top.)

---

