---
title: "Ralink RT3290LE: low sensitivity, connection loss and causes reboot of system"
date: 2016-08-26
forum: Networking &amp; Wireless
---

### Post by mf-linux on 2016-08-26
Problems with "Ralink RT3290LE 802.11bgn 1x1 Wifi and Bluetooth 4.0 Combo Adapter" and ubuntu 16.04:

1- If the wifi card is turned on when you order shutdown of the system (from terminal, shutdown button, etc.), the result is always a restart. To shutdown the laptop, one must disable previously the wifi card.

2- Low sensitivity to wifi signal, sometimes losing connection intermittently. In my case, at 3 meters from the router, without obstacles in between, signal strength ranges from only 51 to 63%. Speed tests show really lower speed, specially for download (I compared this card with an usb wifi dongle) 

3- Sometimes the wifi card loses the connection and remains deactivated, no matter what you do; if you simply restart the system, it is impossible to turn it on; by contrast, if you make a shutdown instead of a restart, the wifi card works again.

I'm experiencing all of these issues with a HP Envy m6-1202ss and ubuntu 16.04. Lower sensitivity and connection loses are there since ubuntu 15.04. Restarts of the system when you want to shutdown, I think began with update to kernel 3.9., also in 15.04.

Probably all is related with the kernel driver.

I transiently "solved" all the problems by using a TP-Link Nano Usb Adapter (TL-WN725N), which runs perfectly, and disabling the PCI wifi card.

Hope someone can find a real solution for a persistently (as I've seen from other posts) problematic wifi card. I've tried previously and unsuccessfully, among others: [https://ubuntuforums.org/showthread.php?t=2104129&page=2](https://ubuntuforums.org/showthread.php?t=2104129&page=2),
[https://ubuntuforums.org/showthread.php?t=2325855&highlight=ralink+rt3290](https://ubuntuforums.org/showthread.php?t=2325855&highlight=ralink+rt3290), [http://askubuntu.com/questions/258233/how-do-i-get-the-ralink-wireless-controller-working-on-an-hp-envy-7212nr](http://askubuntu.com/questions/258233/how-do-i-get-the-ralink-wireless-controller-working-on-an-hp-envy-7212nr), [http://onthim.blogspot.com.es/2015/06/install-ralink-rt3290-wi-fi-driver-on.html](http://onthim.blogspot.com.es/2015/06/install-ralink-rt3290-wi-fi-driver-on.html)


Thank you in advance


[ATTACH]270877[/ATTACH]

Info supplied by "sudo lshw -class network":
*-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 00
       serial: b8:76:3f:3a:49:fd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.4.0-21-generic firmware=0.37 ip=192.168.1.50 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0110000-f011ffff

---

