---
title: "Ipw2200 Wep"
date: 2005-08-30
forum: Networking &amp; Wireless
---

### Post by cbudden on 2005-08-30
Hello.  Please forigive if this has been posted before but i couldn't find anything while searcing.

When I have WEP encryption turned off, i can connect to my wireless network fine.  When i turn it on on the router and do this iwconfig eth1 key #######, then dhclient or a restart, the card doesn't connect.  Any ideas?

---

### Post by luca_linux on 2005-08-30
The key must be entered in hexadecimal, otherwise, if it's in ascii, you have to put it in quotes ("your_key").
Anyway, the driver coming with Hoary (version 0.19) is obsolete and a little bit buggy, maybe you'd like to update it to the latest version (1.0.6). Just follow the first part of this HowTo: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

---

### Post by cbudden on 2005-08-30
[QUOTE=luca_linux]The key must be entered in hexadecimal, otherwise, if it's in ascii, you have to put it in quotes ("your_key").
Anyway, the driver coming with Hoary (version 0.19) is obsolete and a little bit buggy, maybe you'd like to update it to the latest version (1.0.6). Just follow the first part of this HowTo: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

Thanks.  I already updated to 1.0.6(btw, how do i check the current version?)

Also big thanks as my Wep does work now!

---

### Post by cbudden on 2005-08-30
[QUOTE=cbudden]Thanks.  I already updated to 1.0.6(btw, how do i check the current version?)

Also big thanks as my Wep does work now![/QUOTE]
 After i put wep on and am surfing using it, when i restart my laptop the card cannot connect!

---

### Post by luca_linux on 2005-08-30
Type "dmesg | grep ipw" (obviously without the quotes) and then post the result.

---

### Post by cbudden on 2005-08-30
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

thanks

---

