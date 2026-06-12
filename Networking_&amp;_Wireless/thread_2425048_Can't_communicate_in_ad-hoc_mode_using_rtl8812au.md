---
title: "Can't communicate in ad-hoc mode using rtl8812au"
date: 2019-08-19
forum: Networking &amp; Wireless
---

### Post by o1111111o on 2019-08-19
[FONT=arial]Hello, 
During test for wireless ad-hoc mode, I ask a question as it doesn't work.

I'm using 3 nvidia jetson nano boards and 3 Archer T4UHP for wireless module.
After installing rtl8812au driver from [/FONT][https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au), I checked normal wifi connection is no problem. 
But in ad-hoc mode the boards can't communicate each other even though they are in same essid, cell, frequency...

It is because the driver wasn't installed properly or the compatibility between realtek chipset and ubuntu? 
I don't know the reason.

I attached boards' wireless-info.tar.gz.

Plz help...

[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2019-08-19
You should ask the maintainer of the github project what the issue might be.  I do know that project supports multiple chipsets, the 8812AU, 8814AU, and the 8821AU

---

