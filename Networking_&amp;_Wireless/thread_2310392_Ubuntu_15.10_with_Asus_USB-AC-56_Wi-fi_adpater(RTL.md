---
title: "Ubuntu 15.10 with Asus USB-AC-56 Wi-fi adpater(RTL8812AU) very slow connection"
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by carlob2 on 2016-01-18
Hello to everybody,
I have an issue with my Asus Usb3.0 adapter.
After many tries by reading on many-many forums people with the same issue I had, this Usb Wi-fi adapter was successfully installed downloading the driver from github.

uname -r = 4.2.0-23-generic

**But**, There is always a "BUT"......the internet connection is 1.5Mb/sec. instead of 16Mb/sec. (Tested with Speed Test.net)

I have Ubuntu 15.10 along with Windows 10 in dual-boot so, this usb 3.0 adapter is shared between them; with Win10 works fine.
And I have Ubuntu 15.10 installed also on a Notebook Dell 5400, it works perfectly around 16Mb/sec (built-in Wi-Fi adapter).
Sometimes, the connection goes down. Signal level is slow as well: with  WIN 10 I have max signal coverage because the router is not so far from  to the PC (few meters), instead with Ubuntu I have a low level of  coverage

On the Ubuntu PC with the USB-Viewer, I found a strange thing. The usb Version used is 2.0 instead of 3.0 (is it normal ?)
802.11n NIC
Manufacturer: Realtek
Serial Number: 123456
Speed: 480Mb/s (high)
[U][B]USB Version:  2.00
[/B][/U]Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 0b05
Product Id: 17d2
Revision Number:  0.00

I have attached here wireless-info.txt file,
hoping someone may help me.

Thanks a lot
Regards
Carlo

---

