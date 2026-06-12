---
title: "ZTE AC2792 USB Modem not working in Ubuntu 11.10"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by lmrajeev on 2013-11-09
I recently bought a ZTE AC2792 USB modem and it is not working in Ubuntu 11.10. The Network Manager is able to detect the modem, but not able to make a connection. Looks like the system is still treating the device as a USB storage. Tried to switch mode using Sakis3g, but no luck. lsusb displays the same before and after mode switching with Sakis3g.

Here is what lsusb gives for the device :

*Bus 001 Device 008: ID 19d2:fffe ONDA Communication S.p.A. *

Here is what reported by usb-devices :

[I]T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fffe Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Tech
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

[/I]Here is output of uname -a :[I]
Linux edoot-Acer-AOD270 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
[/I]
Has anyone fixed this issue before or have any solution?

---

### Post by sanderj on 2013-11-09
Ubuntu 11.10 is not supported nor updated anymore. See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

I would do this: live-boot Ubuntu 13.10 from a persistent USB-stick, and see if your ZTE AC2792 USB modem works there.

---

### Post by Bucky Ball on 2013-11-09
And I would install 12.04 LTS which is supported until 2017 rather than for the next eight months since it seems like you don't like to upgrade to the next release often. The interim releases are supported for nine months, LTS for five years, and updating from one LTS to the next is a one click process through Update Manager.

You won't get much help with 11.10 as not used as, mentioned above, no longer supported (died April this year).

---

