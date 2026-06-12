---
title: "Troubleshooting wireless (part. Broadcom)"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by crazybilly on 2007-09-08
Since updated to the 2.6.20 kernel, I'm having troubles with my Broadcom wireless.  Before, it worked just fine if I:

a) blacklisted bcm43xx
b) built ndiswrapper from source
c) used wi-fi radar

Since updating, I had to rebuild ndiswrapper.  After rebooting, it worked.  In fact, it was faster, and my wifi indicator light flashed on activity rather than just always being on.

But then I hibernated a/o rebooted.  And now it's not working at all.  It's recognized (iwconfig picks up eth1 as a wireless extension, and Network Monitor recognizes it as a wirelss device).

However scanning w/ iwlist returns  "No scan results" and wi-fi radar bombs out when trying to connect (as does dhclient).

The driver is in (as per modprobe-removing it turns eth1 off).

In dmesg, the related lines are:

[  335.760000] ndiswrapper: using IRQ 22
[  335.976000] wlan0: ethernet device 00:14:a4:14:46:e1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[  335.976000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  335.984000] usbcore: registered new interface driver ndiswrapper
[  336.076000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  336.248000] sis900.c: v1.08.10 Apr. 2 2006
[  336.256000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[  336.264000] 0000:00:04.0: Using transceiver found at address 13 as default
[  336.268000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:b4:68:d6.
[  336.796000] ADDRCONF(NETDEV_UP): eth1: link is not ready

In short, I have no idea how to trouble shoot this.  I'm a lot farther down the Linux road than I used to be (I knew to check dmesg), but I'm still kind of clueless about how to figure things out.   I took a look at the wifi troubleshooting guide (at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)), but it didn't give me much in the way of solutions (beyond the fact that I know that my driver IS installed).

Any ideas of how to troubleshoot this?  

Thanks, ya'll!

---

