---
title: "Linksys WPC11 ver.3 + WPA + NetworkManager + Feisty?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-05-15
My ideal scenario would be to get my WPC11 v.3 wireless card working in Ubuntu Feisty Fawn with NetworkManager and WPA.

Does anyone happen to know what the most efficient way from point A (where I am now, with the stock install that only can connect to unencrypted and WEP APs) to point B (as I've described)?

I've read some other posts about this card, but they weren't exactly applicable to all of: Feisty, NetworkManager, WPC11 v.3, _and_ WPA.

Thanks,
Jamie

[SIZE="1"][COLOR="LemonChiffon"]WPC11 v.3
WPC11 version 3
WPC11 v3[/COLOR][/SIZE]

---

### Post by tturrisi on 2007-05-16
The wpc11 v3 has a prism chipset and works using the orinoco driver that comes w/ linux and comes w/ ubuntu.  You cannot use WPA w/ this card because it is an 80211b device, which can only use WEP.  WPA requires an 80211b-g or a-g device.  "g" devices are backward compatable w/ "b".
see the data sheet here:
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416828350&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2835039789B05](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416828350&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2835039789B05)

---

### Post by Jamie Jackson on 2007-05-16
I don't suppose it makes any difference that I've gotten this card working with WPA under windows, does it?

Thanks,
Jamie

---

### Post by tturrisi on 2007-05-16
> **Jamie Jackson said:**
> I don't suppose it makes any difference that I've gotten this card working with WPA under windows, does it?

Thanks,
Jamie
Then you must be using the newest linksys driver install which upgrades the card's firmware to support WPA, if in fact it does upgrade it.  Most vendors don't have WPA firmware patches or upgrades for 80211b devices.  The firmware upgrade could also be a "software" upgrade and you'll need more than just a windows driver to get it running in linux, you'll need the firmware too.  But according to linksys, the device supports only WEP 128 bit and the newest driver read-me says nothing about WPA.

---

### Post by wieman01 on 2007-05-16
> **Jamie Jackson said:**
> I don't suppose it makes any difference that I've gotten this card working with WPA under windows, does it?

Thanks,
Jamie
Yes, it does. You could install "ndiswrapper" and make use of driver for Windows... Just a thought.

---

### Post by tturrisi on 2007-05-16
here's the linksys driver for windows which added support for wpa:
[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874576896&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993435852B01](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874576896&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993435852B01)

---

### Post by Jamie Jackson on 2007-05-16
Thanks a lot for the info so far. The download has both "NT4" and "XP" drivers. Does it matter which I choose?
```

|-- WPC11v3.0 Driver 060503
|   |-- AUTORUN.INF
|   |-- AutoRun
|   |   |-- FBase.bin
|   |   |-- LINKSYS.ICO
|   |   |-- LSWLUSB.SYS
|   |   |-- PCANDIS3.VXD
|   |   |-- PCANDIS4.SYS
|   |   |-- PCANDIS5.SYS
|   |   |-- SetupWizard.bin
|   |   |-- SetupWizard.exe
|   |   |-- SetupWizard.ini
|   |   |-- W32N50.dll
|   |   |-- borlndmm.dll
|   |   |-- cc3250mt.dll
|   |   `-- msvcp60.dll
|   |-- LSWL2NDS.INF
|   |-- LSWLNDS.CAT
|   |-- LSWLNDS.SYS
|   |-- LSWLNDS5.cat
|   |-- LSWLNDS5.inf
|   |-- LSWLNDSX.SYS
|   |-- Quick Installation
|   |   `-- WPC11 ver3 quick install for 98, Me, 2000, XP.pdf
|   |-- ReadMe.txt
|   |-- SETUP.EXE
|   |-- Utility
<snip>
|   |-- WPC11v3 Release Note 060503 WPA.txt
|   |-- WinNT40
|   |   |-- LSWL.dll
|   |   |-- LSWLND4.sys
|   |   `-- OEMSETUP.INF
|   `-- WinXP
|       |-- LSWLNDS.CAT
|       |-- LSWLNDS5.INF
|       `-- LSWLNDSX.SYS
`-- wpc11v3.0_wpa_dr.exe

```

---

### Post by Jamie Jackson on 2007-05-16
Admittedly, I don't know what I'm doing, but I tried each of them, but got "invalid driver"

This makes me also wonder whether the machine is even aware of the PCMCIA card at the moment. Would lspci list that, or is that some other command?

Thanks,
Jamie

```

jamie@satubuntu:~/Desktop/wpc11$ sudo ndiswrapper -i WPC11v3.0\ Driver\ 060503/LSWLNDS5.inf 
installing lswlnds5 ...

jamie@satubuntu:~/Desktop/wpc11$ ndiswrapper -l
lswlnds5 : invalid driver!
*lswlnds5 : invalid driver!

jamie@satubuntu:~/Desktop/wpc11$ sudo ndiswrapper -i WPC11v3.0\ Driver\ 060503/WinNT40/OEMSETUP.INF 
installing oemsetup ...
couldn't find SourceDisksFiles section - continuing anyway...
couldn't get manufacturer section - installation may be incomplete

jamie@satubuntu:~/Desktop/wpc11$ ndiswrapper -l
lswlnds5 : invalid driver!
*lswlnds5 : invalid driver!
oemsetup : invalid driver!

jamie@satubuntu:~/Desktop/wpc11$ sudo ndiswrapper -i WPC11v3.0\ Driver\ 060503/LSWL2NDS.INF 
installing lswl2nds ...

jamie@satubuntu:~/Desktop/wpc11$ ndiswrapper -l
lswl2nds : invalid driver!
lswlnds5 : invalid driver!
*lswlnds5 : invalid driver!
oemsetup : invalid driver!

```

---

