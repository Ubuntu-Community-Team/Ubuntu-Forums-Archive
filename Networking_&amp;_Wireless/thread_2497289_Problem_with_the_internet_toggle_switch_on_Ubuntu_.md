---
title: "Problem with the internet toggle switch on Ubuntu: inactive"
date: 2024-04-29
forum: Networking &amp; Wireless
---

### Post by hark781 on 2024-04-29
There is no wired network option in the settings in **Ubuntu Desktop 24.04**, even after upgrading from the previous version **23.10** (which I completely uninstalled and reinstalled). This seems to be an old problem found in many releases. After installing **Ubuntu Desktop 24.04**, I can't find the settings for a wired connection, although wireless internet access is present. Disabling the wireless connection results in no internet at all. However, the Ethernet cable works: in the same **Windows 11** computer, wired internet is available. The Ethernet LEDs also indicate a connection, and a previously installed **Ubuntu Desktop 23.04** “***Lunar Lobster***” successfully connected via Ethernet. This suggests that the problem is related to the Ubuntu software.

```
[COLOR=#000000][FONT=&amp]*-network                 [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Tiger Lake PCH CNVi WiFi[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 14.3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1089;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1086; &#1096;&#1080;&#1085;&#1077;: pci@0000:00:14.3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: wlo1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 11[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 14:18:c3:e4:76:45[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress msix bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=iwlwifi driverversion=6.8.0-31-generic firmware=77.ad46c98b.0 QuZ-a0-hr-b0-77.u ip=192.168.0.39 latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: iomemory:600-5ff IRQ:16 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:6001114000-6001117fff[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: RTL8125 2.5GbE Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1089;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1086; &#1096;&#1080;&#1085;&#1077;: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: enp3s0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 05[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: d8:5e:d3:58:e6:00[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.8.0-31-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 link=no multicast=yes port=twisted pair[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:18 ioport:3000(&#1088;&#1072;&#1079;&#1084;&#1077;&#1088;=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:3f900000-3f90ffff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:3f910000-3f913fff[/FONT][/COLOR]
```

---

