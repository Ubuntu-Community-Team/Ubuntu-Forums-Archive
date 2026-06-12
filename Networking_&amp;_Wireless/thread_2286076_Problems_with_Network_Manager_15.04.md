---
title: "Problems with Network Manager 15.04"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by 7-webmaster on 2015-07-09
I am having numerous annoying issues with the Network Manager app on 15.04:

[LIST]
[*]Sometimes when I resume after suspend (e.g. open laptop cover) the Network Manager icon is missing and I cannot start any network connections without rebooting
[*]Even if the NM icon is present it doesn't seem to work properly.
[/LIST]
For example at the moment even though I rebooted the system from powered off, the NM app is not working.  It has connected to the wired connection and changed the appearance of the icon to the bidirectional arrows, but it has not activated the wireless connection even though I have several times explicitly asked it to activate that connection.  Moreover when I actually ask it for a list of connections it says there are NO connections, even though the wired connection is actually working.  Moreover if I ask to edit the connections it comes back and says there are no connections to edit.  I even tried the command line interface, which displays:

```
:~$ nmcli -p g
===========================================================
                   NetworkManager status
===========================================================
STATE    CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
-----------------------------------------------------------
unknown  unknown       unknown  unknown  unknown  unknown 
:~$ nmcli -p n
==============
  Networking
==============
NETWORKING 
--------------
unknown    
:~$ nmcli -p r
====================================
           Radio switches
====================================
WIFI-HW  WIFI     WWAN-HW  WWAN    
------------------------------------
unknown  unknown  unknown  unknown 
```

---

### Post by gordintoronto on 2015-07-10
To obtain information about networking, I would normally use the command: ifconfig -a

People might be able to give you more help if you identified the brand and model of the laptop, and the exact version of Linux you are using. (Ubuntu 15.04 64-bit?)

Actually, you might find the answer with a good Google query such as: HP G62 suspend network linux

---

### Post by 7-webmaster on 2015-07-10
Further information, this is on a Dell Vostro 3555, approximately a 4  year old device, so not exactly a bleeding edge piece of hardware.  Also sometimes the USB ports are dead after  resume.  However at least the display hardware now works thanks  presumably to the improvements in support for AMD graphics in kernel  3.19 and maybe also to Systemd handling of resume.

---

