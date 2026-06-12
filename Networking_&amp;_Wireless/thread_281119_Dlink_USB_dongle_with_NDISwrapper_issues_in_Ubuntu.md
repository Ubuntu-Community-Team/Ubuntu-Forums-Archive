---
title: "Dlink USB dongle with NDISwrapper issues in Ubuntu"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Forbuto on 2006-10-20
Hi all,

Sooo I've installed Dapper on an old system depending on a Dlink DWL-G122 (ver c1) USB dongle device for wireless internet access.

I've been trying to use Ndiswrapper to set the device up and am not having any luck.  I've removed installed the new Ndiswrapper, removed the default installed one, and installed the most recent windows drivers (NetRtUsb.inf file) successfully but im stuck when do an "ndiswrapper -l" and only see "Driver installed".  There is nothing indicating "hardware is present" as all instrucitons have indicated i should see.  My usb hardware is detected by the OS as i see it when i list 'lsusb'.

Does anyone have any idea why the hardware just isnt picking up when i install the driver with ndiswrapper? Ill have to apologize for not pasting screen outputs but i will do so when im home and around the machine.  any help is greatly appreciated.

thanks
-F

---

### Post by wieman01 on 2006-10-20
When you deploy the *.INF file, are all other driver files (e.g. *.SYS, etc.) in the same folder as *.INF? If that was not the case, try to install the Windows driver once again bearing that in mind.

---

### Post by tturrisi on 2006-10-21
the dongle has a ralink chipset, see:
[http://forums.ralinktech.com.tw/phpbb2/viewtopic.php?t=2369](http://forums.ralinktech.com.tw/phpbb2/viewtopic.php?t=2369)
(don't use link in last post of that thread, seeems to be pron related)

---

