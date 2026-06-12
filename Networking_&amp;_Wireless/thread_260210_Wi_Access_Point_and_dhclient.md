---
title: "Wi Access Point and dhclient"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Kurdt on 2006-09-18
Hi, i followed this guide for setting up RT61 chip [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

in last part says:

> dhclient ra0

i do too have the error "No DHCPOFFERS received." BUT, my AP DOES NOT provide DHCP, other router in the same network does:

```

      Router (With DHCP Server)
      |
      |
      AP
    |      |
    |      |
    XP    Ubuntu
```

In this situation the AP is just like another hub on the network , so, do i have to use dhclient command? (I think i do, but something is wrong here)
If i want to obtain an IP address from the router's lease i have to pass through AP, so?

**I have another computer with Windows XP on the network and it CAN obtain an IP address from router through Access Point, and it uses DHCP client**

I hope you understand my explanation,

PS: I am using 2.6.15-26-amd64-generic, and patched rtmp_data.c to support amd64.
The Access Point is a MSI RG54GS2
The PCI Card is a MSI PC54G3
I have entry logs in my AP telling me that some handshake is being done between ubuntu and the AP.
> 
lun 18 sep 2006 13:44:28 ART	 Associated: 00-13-D3-7A-DD-C6 st=0
lun 18 sep 2006 13:44:31 ART	DHCP:discover(msirouter)
lun 18 sep 2006 13:46:07 ART	DOD:triggered internally

Thanks!

EDIT: i am using WPA Based auth.

---

### Post by Kurdt on 2006-09-21
Well, i think i have the same problem with RT61 based cards, that can't do WPA auth, is there some solution to this ? Thanks

[http://www.ubuntuforums.org/showthread.php?t=132980&highlight=](http://www.ubuntuforums.org/showthread.php?t=132980&highlight=)

---

### Post by huygens on 2006-11-19
I have been following [these instructions]("http://ubuntuforums.org/showthread.php?t=296822") and got WPA working with DHCP.
I have also a RT61 card (MSI PC54G3).

Huygens

---

