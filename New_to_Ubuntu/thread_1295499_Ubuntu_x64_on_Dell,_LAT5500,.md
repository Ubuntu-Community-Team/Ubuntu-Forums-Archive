---
title: "Ubuntu x64 on Dell, LAT5500,"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by manouchehr on 2009-10-19
Hello Dears, I want to Install Ubuntu x64 on my machine anyone can please let me know that my machine support, below is my machine info.


OS Name    Microsoft Windows 7 Ultimate
Version    6.1.7100 Build 7100
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    MANOUCHEHRSH-PC
System Manufacturer    Dell Inc.
System Model    Latitude E5500
System Type    x64-based PC
Processor    Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz, 2001 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date    Dell Inc. A13, 8/11/2009
SMBIOS Version    2.4
Windows Directory    C:\Windows
System Directory    C:\Windows\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "6.1.7100.0"
User Name    ManouchehrSh-PC\Manouchehr
Time Zone    Pacific Daylight Time
Installed Physical Memory (RAM)    3.00 GB
Total Physical Memory    2.96 GB
Available Physical Memory    1.93 GB
Total Virtual Memory    5.91 GB
Available Virtual Memory    4.77 GB
Page File Space    2.96 GB
Page File    C:\pagefile.sys


Kind Regards

---

### Post by QIII on 2009-10-19
Your machine looks good with the following caveat:

You are running Intel Graphics, which have been problematic in Jaunty Jackalope (9.04)

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Read down to the section about performance regressions on Intel graphics cards.

Do you plan to do a dual-boot (that is, do you want to continue to maintain Windows 7 along side Ubuntu)?

If you do, please read the following carefully:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This is written with Vista in mind, so it might be worth a bit more research.

---

