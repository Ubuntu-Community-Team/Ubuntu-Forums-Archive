---
title: "Ubuntu Time Shift"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by ebates on 2010-02-18
Why does Ubuntu 9.10 reset my system time forward 18 hrs.
Intro: Well versed in hardware and Windows, clueless to this point in Linux.  I do all or the hardware and Windows repair/upgrades for my family and extended family, and have for years.
Why does Ubuntu 9.10 reset my system time forward 18 hrs.
I read somewhere that using a time server could cause this. Disabled the time servers in windows and Ubuntu and still each time I run winxp pro after running Ubuntu the BIOS clock has been reset.  Any clues?

Tx
EBates

---

### Post by wmcbrine on 2010-02-18
Best guess: Ubuntu thinks your system clock is set to GMT, but it's actually set to local time.

---

### Post by ebates on 2010-02-18
> **ebates said:**
> Why does Ubuntu 9.10 reset my system time forward 18 hrs.
Intro: Well versed in hardware and Windows, clueless to this point in Linux.  I do all or the hardware and Windows repair/upgrades for my family and extended family, and have for years.
Why does Ubuntu 9.10 reset my system time forward 18 hrs.
I read somewhere that using a time server could cause this. Disabled the time servers in windows and Ubuntu and still each time I run winxp pro after running Ubuntu the BIOS clock has been reset.  Any clues?

Tx
EBates
In my infinite ignorance I have checked the Ubuntu clock settings from top to bottom, Time Zone appears to be correct and the time setting appears correct and as nearly as I can tell Syncronization is off.

---

### Post by adam814 on 2010-02-18
+1

That's exactly right.  Windows by default sets the system clock to local time.  Ubuntu by default uses GMT.  As of Vista you can't set Windows to use GMT anymore, so your only option would be to set Ubuntu to use local time.

Here's how:
[https://help.ubuntu.com/community/UbuntuTime#Make%20Linux%20use%20%27Local%27%20time]("https://help.ubuntu.com/community/UbuntuTime#Make%20Linux%20use%20%27Local%27%20time")

Then you can set the clock yourself (you may get warnings that some files have timestamps in the future).  After that if you want you can use NTP servers.

---

### Post by marshmallow1304 on 2010-02-18
[http://ubuntuforums.org/showpost.php?p=2283891](http://ubuntuforums.org/showpost.php?p=2283891)


Edit: Beaten by seconds.  +1 for finding the official documentation.

---

### Post by adam814 on 2010-02-18
> **ebates said:**
> In my infinite ignorance I have checked the Ubuntu clock settings from top to bottom, Time Zone appears to be correct and the time setting appears correct and as nearly as I can tell Syncronization is off.


It's not that the wrong time zone is selected, it's that Linux normally stores the system clock in GMT and interprets it to give the correct local time.  If the system time is in fact local time (as Windows stores it) and Ubuntu isn't aware of it, it will adjust the local time as if it were GMT and display the wrong time.

---

### Post by ebates on 2010-02-18
Thanks to all you fine folks for the shared knowledge.
A quick edit of the rcS file and no more time shifting (I hope).

Tx
EBates

---

### Post by wmcbrine on 2010-02-18
> **adam814 said:**
> As of Vista you can't set Windows to use GMT anymoreWow, lame. I didn't even realize that Windows ever allowed GMT, but it seems to be moving in the wrong direction. :(

---

### Post by adam814 on 2010-02-19
> **wmcbrine said:**
> Wow, lame. I didn't even realize that Windows ever allowed GMT, but it seems to be moving in the wrong direction. :(

Well, fortunately it still does for people who happen to live in that time zone.  I'm sure this will be billed as a feature in those markets soon enough.

---

