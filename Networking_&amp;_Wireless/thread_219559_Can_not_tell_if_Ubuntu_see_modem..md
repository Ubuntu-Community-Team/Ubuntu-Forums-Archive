---
title: "Can not tell if Ubuntu see modem."
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by gargoyle on 2006-07-20
I originally posted in the  Absolute Beginner Talk but received no replies so I am posting it here.

The modem in question is Zoom internal 56k LT.
The modem is located in dual boot box, I verified it works with Winxp.

WinXp report the modem is set to Comm 4.

I can not verify the Ubuntu even see the modem. I have tried the
System
Device Manager

I do not see any listing for a modem at all.

Is there any other way to see what hardware I have?

---

### Post by swamytk on 2006-07-20
$sudo lspci

check the result for any device string which says that it is a communication controller/modem/..

seems to be winmodem, be prepared to work hard to make it work in linux

---

### Post by gargoyle on 2006-07-20
To swamytk;
No it is not a winmodem it is a hardware modem but it is rather old.
Results of lspci:
ed100@ed100-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master  IDE (rev 06)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Ad apter

I do not see any listing for it. I do see a listing for th ISA bus on which it sits.

So if it does not see what next?

---

### Post by swamytk on 2006-07-20
This is a official page of Zoom for linux support. Did you check this?

[http://www.zoom.com/techsupport/dial_up/linux.shtml](http://www.zoom.com/techsupport/dial_up/linux.shtml)

---

