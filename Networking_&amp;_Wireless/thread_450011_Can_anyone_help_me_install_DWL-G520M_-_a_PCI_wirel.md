---
title: "Can anyone help me install DWL-G520M - a PCI wireless card?"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by oliu on 2007-05-20
Hi,
   I just downloaded the latest 7.0.4 dvd build and tried installing it on my newly built machine. Everything is working Ok except my old wireless pci card. So here is my problem:

   PCI Wireless Card: DWL-G520M
   Motherboard: MB ASUS M2NBP-VM CSM NVS 210S AM2
   Ubuntu: 7.0.4 
   Kernel: 2.6.20-15 generic #2 SMP

   Problem is that I can't find it name in my Hardware list and lspci didn't show it neither.

   I already had 2 NIC (One comes with the MB and the other is my old Zxy Gigabyte NIC), will that be a problem? My other Zxy Gigabyte NIC is a PCI card and was recognized by OS with no problem.

Thanks for the help
Ou

---

### Post by scrooge_74 on 2007-05-20
Check the supported cards list first

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by oliu on 2007-05-20
Well, I have checked the list, it shows that DWL-G520 and DWL-G520+ are both supported while DWL-G520m is not. Does that mean the DWL-G520m is NOT supported? If that's the case, I guess Ubuntu should also establish a list of NOT supported hardware list and once later on the support is there, people can move it to supported list.

---

### Post by scrooge_74 on 2007-05-21
There are so many pieces of hardware that the list would get rather long.  If something is not there then it means there are probably no linux drivers.

What it means is that you are most likely have to use something like ndiswrapper to use the windows drivers in order for you to use it.

---

### Post by Kobalt on 2007-05-21
I think you will need to use [MadWifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") in order to get your card working (though I'm not sure it will).

---

