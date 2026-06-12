---
title: "wlan0 up but no browser"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by bobterri on 2005-11-05
My wlan0 seems to be working.  I installed ndiswrapper according the the ubuntu wiki and installation went fine.  Iwconfig and "network settings" both show that the Broadcom wireless card is recognized and working.  Still, when I open a browser I get nothing.  Am I missing something somewhere?  Wireless on this laptop worked with Mandrake 10.1 and Suse 9.2.

---

### Post by skmassey on 2005-11-06
Are you recieveing an IP address and DNS servers?  Maybe post your output for "ifconfig wlan0"

---

### Post by bobterri on 2005-11-06
I went with the linuxant driver and all is working well.

---

