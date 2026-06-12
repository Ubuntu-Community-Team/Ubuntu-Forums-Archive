---
title: "DWL-G122 no wireless network"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by kosiew on 2005-10-23
I just intalled ubuntu 5.10 and am trying to connect to a home wireless network with a D-Link USB adapter DWL-G122.

Currently, 
  iwconfig
  
    lo       no wireless extensions
    eth0   no wireless extensions
    sit0    no wireless extensions

  lsusb
    Bus 001 Device 004: ID2001:3c00 D-Link Corp. [hex]

   But the adapter does not light up as when I use it on Windows XP. The adapter works fine when I dual boot to Windows XP.


I have used ndiswrapper to install the XP driver.

After installing:

  ndiswrapper -l
     netrtusb driver present, hardware present

Would appreciate some pointers on what I missed.

Thanks in advance.

---

### Post by carlosqueso on 2005-10-25
I have the same problem with my D-link DWL-650 it sees the hardware, but won't treat it as a network card or turn it on.... anybody have any ideas?

---

