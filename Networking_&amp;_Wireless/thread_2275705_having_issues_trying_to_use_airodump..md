---
title: "having issues trying to use airodump."
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by adhd2 on 2015-04-27
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Everytimei try to hack my own network (white hat) , i keep getting what iassume to be an error message. i successfully switch my wirelessadapter into monitor mode, and then i do this command and this iswhat i get.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]seph80hd@seph80hd-MacBookPro:~$sudo airmon-ng start wlan1[/FONT][/COLOR]




[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Found5 processes that could cause trouble.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Ifairodump-ng, aireplay-ng or airtun-ng stops working after[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]ashort period of time, you may want to kill (some of) them![/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]PID    Name[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]659    NetworkManager[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]676    avahi-daemon[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]770    avahi-daemon[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]816    wpa_supplicant[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]1585  dhclient[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Processwith PID 1585 (dhclient) is running on interface wlan1[/FONT][/COLOR]




[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Interface      Chipset                 Driver[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]wlan0          Broadcom              wl - [phy0][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]wlan1          Unknown                  rtl8812au (monitor mode enabled)[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]seph80hd@seph80hd-MacBookPro:~$sudo airodump-ng mon0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Interfacemon0: [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]ioctl(SIOCGIFINDEX)failed: No such device[/FONT][/COLOR]

---

### Post by QIII on 2015-04-27
Please review the [Ubuntu Forums Rules,]("http://ubuntuforums.org/misc.php?do=showrules") with special attention to:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

We don't allow questions about cracking or pen testing on the forums.  I suggest that [https://forums.kali.org/](https://forums.kali.org/) might be a suitable resource.

Closed.

---

