---
title: "How to install VideoDriver on intel945 ?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by baskar007 on 2009-09-22
i dont know how to install videodrivers for my intel945 chipset. can any one help me?

Screen short of HardwareDrivers:
[IMG]http://img508.imageshack.us/img508/8937/screenshothardwaredrive.png[/IMG]

here some tech details for your refer:
**~$ lspci**
> 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


any ideas guys?

---

### Post by halitech on 2009-09-22
If you are seeing your desktop then you have drivers installed. Just because there are none showing in the Hardware drivers window doesnt mean you need to install any, just means there are no 3rd party (proprietary) drivers available for you.

If you are using 9.04 then you may want to look here if you are having issues with poor video output

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by baskar007 on 2009-09-22
thanks,I will try 
> **halitech said:**
> 
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
and post reply soon.

---

### Post by baskar007 on 2009-09-22
The solution is here:  [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

Thank you for help **halitech**

---

### Post by halitech on 2009-09-22
glad to help out

---

### Post by baskar007 on 2009-09-22
:)

---

