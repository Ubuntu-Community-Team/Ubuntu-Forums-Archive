---
title: "Reduced wireless scanning range 1390 WLAN"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by daedalus0x1a4 on 2009-12-01
Earlier I had been having a problem finding my usual connection after installing Ubuntu 9.10. Under Windows everything was fine, all my neighbors showed up, but under Ubuntu only the two closest (or strongest) signals showed up.

I have an Inspiron 9400 with a Dell 1390 WLAN, which is Broadcom 4311 based. As far as I know these were fairly popular laptops and I noticed a lot of other people having the same problem with no solution.

Anyways, after fooling around with iwconfig and the Broadcom STA driver for a while I decided to just use ndiswrapper to install the windows drivers.

I downloaded the driver from Dells website using my service tag to find it, followed the ndiswrapper howto documentation ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), and now the scanning range is back to what it was in Windows.

I'm not 100% sure if this has been covered or not but I couldn't find the thread so I wanted to put it out there for other people who may be experiencing a similar issue.

:)

---

### Post by running_rabbit07 on 2009-12-02
This might be something that could be added to a Karmic Sticky.

Thanks for the input, I am sure this will prove helpful for some people.

---

