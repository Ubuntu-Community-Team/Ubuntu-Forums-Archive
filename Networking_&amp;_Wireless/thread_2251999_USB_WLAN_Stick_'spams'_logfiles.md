---
title: "USB WLAN Stick 'spams' logfiles"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by mark175 on 2014-11-08
Hello,

my new USB Wireless Stick (TP Link TL-WN727N) starts 'spamming' my log files. Here is an example:


```
Nov  8 15:15:27 Isomaniac kernel: [15290.007113] TssiDC0: -1
Nov  8 15:15:27 Isomaniac kernel: [15290.007118] tssi_offset: -22
Nov  8 15:15:27 Isomaniac kernel: [15290.007122] tssi_offset<<9: -11264
Nov  8 15:15:27 Isomaniac kernel: [15290.007126] TssiSlope: 131
Nov  8 15:15:27 Isomaniac kernel: [15290.007129] tssi_db: 1138
Nov  8 15:15:27 Isomaniac kernel: [15290.007133] CurrentPower: 137814
Nov  8 15:15:27 Isomaniac kernel: [15290.007136] PowerDiff: 5546
Nov  8 15:15:27 Isomaniac kernel: [15290.007140] final PowerDiff: 1(0x1)
Nov  8 15:15:27 Isomaniac kernel: [15290.007460] MAC 13b4: 0xc9540023
Nov  8 15:15:29 Isomaniac kernel: [15292.011356] RtmpUSBNullFrameKickOut - Send NULL Frame @24 Mbps...
Nov  8 15:15:31 Isomaniac kernel: [15294.020473] TSSI = 0x5F
Nov  8 15:15:31 Isomaniac kernel: [15294.020481] temperature = 0xFFFFFFF8
Nov  8 15:15:31 Isomaniac kernel: [15294.020485] PacketType = 0xC
Nov  8 15:15:31 Isomaniac kernel: [15294.020489] tx_11b_rate: 0
Nov  8 15:15:31 Isomaniac kernel: [15294.020493] Channel PWR + MCS PWR = 25000
Nov  8 15:15:31 Isomaniac kernel: [15294.022115] TargetPower: 0x24ccd(150733)
Nov  8 15:15:31 Isomaniac kernel: [15294.022125] tssi_m_dc: 96
Nov  8 15:15:31 Isomaniac kernel: [15294.022129] TssiLinear0: 95
Nov  8 15:15:31 Isomaniac kernel: [15294.022133] TssiDC0: -1
Nov  8 15:15:31 Isomaniac kernel: [15294.022138] tssi_offset: -22
Nov  8 15:15:31 Isomaniac kernel: [15294.022143] tssi_offset<<9: -11264
Nov  8 15:15:31 Isomaniac kernel: [15294.022147] TssiSlope: 131
Nov  8 15:15:31 Isomaniac kernel: [15294.022152] tssi_db: 1269
Nov  8 15:15:31 Isomaniac kernel: [15294.022157] CurrentPower: 154975
Nov  8 15:15:31 Isomaniac kernel: [15294.022162] PowerDiff: -4242
Nov  8 15:15:31 Isomaniac kernel: [15294.022167] final PowerDiff: -1(0xffffffff)
Nov  8 15:15:31 Isomaniac kernel: [15294.022589] MAC 13b4: 0xc9540022
Nov  8 15:15:35 Isomaniac kernel: [15298.034841] TSSI = 0x57
Nov  8 15:15:35 Isomaniac kernel: [15298.034849] temperature = 0xFFFFFFF8
Nov  8 15:15:35 Isomaniac kernel: [15298.034854] PacketType = 0xC
Nov  8 15:15:35 Isomaniac kernel: [15298.034858] tx_11b_rate: 0
Nov  8 15:15:35 Isomaniac kernel: [15298.034862] Channel PWR + MCS PWR = 25000
Nov  8 15:15:35 Isomaniac kernel: [15298.036981] TargetPower: 0x24ccd(150733)
Nov  8 15:15:35 Isomaniac kernel: [15298.036991] tssi_m_dc: 88
Nov  8 15:15:35 Isomaniac kernel: [15298.036995] TssiLinear0: 87
Nov  8 15:15:35 Isomaniac kernel: [15298.037000] TssiDC0: -1
Nov  8 15:15:35 Isomaniac kernel: [15298.037005] tssi_offset: -22
Nov  8 15:15:35 Isomaniac kernel: [15298.037010] tssi_offset<<9: -11264
Nov  8 15:15:35 Isomaniac kernel: [15298.037014] TssiSlope: 131
Nov  8 15:15:35 Isomaniac kernel: [15298.037018] tssi_db: 1245
Nov  8 15:15:35 Isomaniac kernel: [15298.037023] CurrentPower: 151831
Nov  8 15:15:35 Isomaniac kernel: [15298.037027] PowerDiff: -1098
Nov  8 15:15:35 Isomaniac kernel: [15298.037033] final PowerDiff: 0(0x0)
Nov  8 15:15:35 Isomaniac kernel: [15298.037613] MAC 13b4: 0xc9540022
Nov  8 15:15:39 Isomaniac kernel: [15302.049728] RtmpUSBNullFrameKickOut - Send NULL Frame @24 Mbps...
Nov  8 15:15:43 Isomaniac kernel: [15306.062597] TSSI = 0x57
Nov  8 15:15:43 Isomaniac kernel: [15306.062606] temperature = 0xFFFFFFF8
Nov  8 15:15:43 Isomaniac kernel: [15306.062610] PacketType = 0xC
Nov  8 15:15:43 Isomaniac kernel: [15306.062614] tx_11b_rate: 0
Nov  8 15:15:43 Isomaniac kernel: [15306.062618] Channel PWR + MCS PWR = 25000
Nov  8 15:15:43 Isomaniac kernel: [15306.066598] TargetPower: 0x24ccd(150733)
Nov  8 15:15:43 Isomaniac kernel: [15306.066606] tssi_m_dc: 88
Nov  8 15:15:43 Isomaniac kernel: [15306.066610] TssiLinear0: 87
Nov  8 15:15:43 Isomaniac kernel: [15306.066613] TssiDC0: -1
Nov  8 15:15:43 Isomaniac kernel: [15306.066617] tssi_offset: -22
Nov  8 15:15:43 Isomaniac kernel: [15306.066621] tssi_offset<<9: -11264
Nov  8 15:15:43 Isomaniac kernel: [15306.066624] TssiSlope: 131
Nov  8 15:15:43 Isomaniac kernel: [15306.066628] tssi_db: 1245
Nov  8 15:15:43 Isomaniac kernel: [15306.066631] CurrentPower: 151831
Nov  8 15:15:43 Isomaniac kernel: [15306.066635] PowerDiff: -1098
Nov  8 15:15:43 Isomaniac kernel: [15306.066639] final PowerDiff: 0(0x0)
Nov  8 15:15:43 Isomaniac kernel: [15306.066962] MAC 13b4: 0xc9540022
Nov  8 15:15:47 Isomaniac kernel: [15310.080597] TSSI = 0x3C
Nov  8 15:15:47 Isomaniac kernel: [15310.080605] temperature = 0xFFFFFFF8
Nov  8 15:15:47 Isomaniac kernel: [15310.080609] PacketType = 0x95
Nov  8 15:15:47 Isomaniac kernel: [15310.080613] tx_11g_rate: 9
Nov  8 15:15:47 Isomaniac kernel: [15310.080618] Channel PWR + MCS PWR = 22000
Nov  8 15:15:47 Isomaniac kernel: [15310.081215] TargetPower: 0x23000(143360)
Nov  8 15:15:47 Isomaniac kernel: [15310.081220] tssi_m_dc: 61
Nov  8 15:15:47 Isomaniac kernel: [15310.081224] TssiLinear0: 60
Nov  8 15:15:47 Isomaniac kernel: [15310.081227] TssiDC0: -1
Nov  8 15:15:47 Isomaniac kernel: [15310.081232] tssi_offset: -22
Nov  8 15:15:47 Isomaniac kernel: [15310.081235] tssi_offset<<9: -11264
Nov  8 15:15:47 Isomaniac kernel: [15310.081239] TssiSlope: 131
Nov  8 15:15:47 Isomaniac kernel: [15310.081242] tssi_db: 1143
Nov  8 15:15:47 Isomaniac kernel: [15310.081246] CurrentPower: 138469
Nov  8 15:15:47 Isomaniac kernel: [15310.081249] PowerDiff: 4891
Nov  8 15:15:47 Isomaniac kernel: [15310.081253] final PowerDiff: 1(0x1)
Nov  8 15:15:47 Isomaniac kernel: [15310.081676] MAC 13b4: 0xc9540023
Nov  8 15:15:49 Isomaniac kernel: [15312.087484] RtmpUSBNullFrameKickOut - Send NULL Frame @24 Mbps...
Nov  8 15:15:51 Isomaniac kernel: [15314.093344] TSSI = 0x60
Nov  8 15:15:51 Isomaniac kernel: [15314.093352] temperature = 0xFFFFFFF8
Nov  8 15:15:51 Isomaniac kernel: [15314.093357] PacketType = 0xC
Nov  8 15:15:51 Isomaniac kernel: [15314.093360] tx_11b_rate: 0
Nov  8 15:15:51 Isomaniac kernel: [15314.093364] Channel PWR + MCS PWR = 25000
Nov  8 15:15:51 Isomaniac kernel: [15314.094838] TargetPower: 0x24ccd(150733)
Nov  8 15:15:51 Isomaniac kernel: [15314.094844] tssi_m_dc: 97
Nov  8 15:15:51 Isomaniac kernel: [15314.094848] TssiLinear0: 96
Nov  8 15:15:51 Isomaniac kernel: [15314.094851] TssiDC0: -1
Nov  8 15:15:51 Isomaniac kernel: [15314.094855] tssi_offset: -22
Nov  8 15:15:51 Isomaniac kernel: [15314.094859] tssi_offset<<9: -11264
Nov  8 15:15:51 Isomaniac kernel: [15314.094862] TssiSlope: 131
Nov  8 15:15:51 Isomaniac kernel: [15314.094865] tssi_db: 1272
Nov  8 15:15:51 Isomaniac kernel: [15314.094869] CurrentPower: 155368
Nov  8 15:15:51 Isomaniac kernel: [15314.094872] PowerDiff: -4635
Nov  8 15:15:51 Isomaniac kernel: [15314.094877] final PowerDiff: -1(0xffffffff)
Nov  8 15:15:51 Isomaniac kernel: [15314.095213] MAC 13b4: 0xc9540022
```

The card is : "Bus 002 Device 003: ID 148f:7601 Ralink Technology, Corp."
The driver i use is: "DPO_MT7601U_LinuxSTA_3.0.0.4_20130913"
System: Ubuntu 12.04, Kernel 3.2.0-69

I had to compile the driver myself and i did not found any option to change the 'logging' behaviour. This makes my /var/log/messages and syslog pretty hard to debug if i look for other problems in the logfiles.

Is there any way to configure the module not to 'spam' the logfiles?

Thanks in advance for any help :)

Greetings,
Mark

---

