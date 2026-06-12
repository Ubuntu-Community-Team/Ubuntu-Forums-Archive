---
title: "Lost and need driver help"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by inoh on 2010-01-05
Trying to get my Laptop up and running dual boot Win Vista and Ubuntu 9.10 Karmic Koala. Been messing around with it for a about a week now and just can't seem to get the hardware working right. I installed it the first time over a week ago. Could not get the atheros ar5007 up to speed with Ubuntu. After several unsuccessful attempts to get the right driver for my wireless and to upgrade to the Nvidia drivers through 190.53 linux pkg1, vista stopped booting. Not the slightest clue of how the Linux drivers could affect the vista MBR. Then I tried to reinstall Ubuntu and end up with two installs and a corrupt GRUB. Unable to figure out the GRUB recovery, I choose to run the Vista recovery disks as even the vista recovery partion was done for. Then I attempted the install Ubuntu again. One more attempt at the right drivers plus some codecs. Still couldn't get things right and somehow managed to make the wireless stop working all together for Ubuntu, allthough the device recognizes. Vista didn't want to boot properly yet again but managed to fix itself.
 
Before I mess anything else up I want to know if anyone can help me fix my laptop.
 
Here is the specs by Vista device manager.
 
```
Compaq Pessario cq60-215dx. System info:
System Information report written at: 01/03/10 18:28:23
System Name: USER-PC
[System Summary]
Item Value 
OS Name Microsoft® Windows Vista™ Home Premium 
Version 6.0.6002 Service Pack 2 Build 6002 
Other OS Description Not Available 
OS Manufacturer Microsoft Corporation 
System Name USER-PC 
System Manufacturer Hewlett-Packard 
System Model Compaq Presario CQ60 Notebook PC 
System Type X86-based PC 
Processor AMD Athlon Dual-Core QL-62, 2000 Mhz, 2 Core(s), 2 Logical Processor(s) 
BIOS Version/Date Hewlett-Packard F.54, 8/18/2009 
SMBIOS Version 2.4 
Windows Directory C:\Windows 
System Directory C:\Windows\system32 
Boot Device \Device\HarddiskVolume1 
Locale United States 
Hardware Abstraction Layer Version = "6.0.6002.18005" 
User Name user-PC\user 
Time Zone Eastern Standard Time 
Installed Physical Memory (RAM) 2.00 GB 
Total Physical Memory 1.75 GB 
Available Physical Memory 1.01 GB 
Total Virtual Memory 3.74 GB 
Available Virtual Memory 2.91 GB 
Page File Space 2.04 GB 
Page File C:\pagefile.sys 
[Hardware Resources]
 
[Conflicts/Sharing]
Resource Device 
I/O Port 0x00000000-0x00000CF7 PCI bus 
I/O Port 0x00000000-0x00000CF7 Direct memory access controller 
 
I/O Port 0x000003C0-0x000003DF PCI standard PCI-to-PCI bridge 
I/O Port 0x000003C0-0x000003DF NVIDIA GeForce 8200M G 
 
IRQ 20 High Definition Audio Controller 
IRQ 20 PCI standard PCI-to-PCI bridge 
IRQ 20 Atheros AR5007 802.11b/g WiFi Adapter 
 
Memory Address 0xC1000000-0xC1FFFFFF PCI standard PCI-to-PCI bridge 
Memory Address 0xC1000000-0xC1FFFFFF NVIDIA GeForce 8200M G 
 
Memory Address 0xFED00000-0xFED003FF High precision event timer 
Memory Address 0xFED00000-0xFED003FF System board 
 
Memory Address 0xC2000000-0xC20FFFFF PCI standard PCI-to-PCI bridge 
Memory Address 0xC2000000-0xC20FFFFF Atheros AR5007 802.11b/g WiFi Adapter 
 
Memory Address 0xC4000000-0xDFFFFFFF PCI standard PCI-to-PCI bridge 
Memory Address 0xC4000000-0xDFFFFFFF NVIDIA GeForce 8200M G 
 
IRQ 16 Standard OpenHCD USB Host Controller 
IRQ 16 Standard Enhanced PCI to USB Host Controller 
 
IRQ 17 Standard OpenHCD USB Host Controller 
IRQ 17 Standard Enhanced PCI to USB Host Controller 
 
Memory Address 0xA0000-0xBFFFF PCI bus 
Memory Address 0xA0000-0xBFFFF PCI standard PCI-to-PCI bridge 
Memory Address 0xA0000-0xBFFFF NVIDIA GeForce 8200M G 
 
I/O Port 0x000003B0-0x000003BB PCI standard PCI-to-PCI bridge 
I/O Port 0x000003B0-0x000003BB NVIDIA GeForce 8200M G 
 
I/O Port 0x00004000-0x00004FFF PCI standard PCI-to-PCI bridge 
I/O Port 0x00004000-0x00004FFF NVIDIA GeForce 8200M G 
 
[DMA]
Resource Device Status 
Channel 4 Direct memory access controller OK 
[Forced Hardware]
Device PNP Device ID 
[I/O]
Resource Device Status 
0x00000000-0x00000CF7 PCI bus OK 
0x00000000-0x00000CF7 Direct memory access controller OK 
0x00000D00-0x0000FFFF PCI bus OK 
0x00000010-0x0000001F Motherboard resources OK 
0x00000022-0x0000003F Motherboard resources OK 
0x00000044-0x0000005F Motherboard resources OK 
0x00000063-0x00000063 Motherboard resources OK 
0x00000065-0x00000065 Motherboard resources OK 
0x00000067-0x0000006F Motherboard resources OK 
0x00000072-0x00000073 Motherboard resources OK 
0x00000074-0x0000007F Motherboard resources OK 
0x00000080-0x00000080 Motherboard resources OK 
0x00000084-0x00000084 Motherboard resources OK 
0x00000091-0x00000093 Motherboard resources OK 
0x00000097-0x0000009F Motherboard resources OK 
0x000000A2-0x000000BF Motherboard resources OK 
0x000000E0-0x000000EF Motherboard resources OK 
0x00000360-0x00000361 Motherboard resources OK 
0x000004D0-0x000004D1 Motherboard resources OK 
0x00000020-0x00000021 Programmable interrupt controller OK 
0x000000A0-0x000000A1 Programmable interrupt controller OK 
0x00000040-0x00000043 System timer OK 
0x0000000A-0x0000000F Direct memory access controller OK 
0x00000081-0x00000083 Direct memory access controller OK 
0x00000087-0x00000087 Direct memory access controller OK 
0x00000089-0x0000008B Direct memory access controller OK 
0x0000008F-0x0000008F Direct memory access controller OK 
0x000000C0-0x000000D1 Direct memory access controller OK 
0x000000D4-0x000000DF Direct memory access controller OK 
0x00000061-0x00000061 System speaker OK 
0x00000070-0x00000071 System CMOS/real time clock OK 
0x000000F0-0x000000F1 Numeric data processor OK 
0x00000060-0x00000060 Standard 101/102-Key or Microsoft Natural PS/2 Keyboard with HP QLB OK 
0x00000064-0x00000064 Standard 101/102-Key or Microsoft Natural PS/2 Keyboard with HP QLB OK 
0x00000062-0x00000062 Microsoft ACPI-Compliant Embedded Controller OK 
0x00000066-0x00000066 Microsoft ACPI-Compliant Embedded Controller OK 
0x00001000-0x0000107F Motherboard resources OK 
0x00001080-0x000010FF Motherboard resources OK 
0x00001200-0x0000127F Motherboard resources OK 
0x00001280-0x000012FF Motherboard resources OK 
0x00001400-0x0000147F Motherboard resources OK 
0x00001480-0x000014FF Motherboard resources OK 
0x00003080-0x000030BF NVIDIA nForce PCI System Management OK 
0x00003040-0x0000307F NVIDIA nForce PCI System Management OK 
0x00003000-0x0000303F NVIDIA nForce PCI System Management OK 
0x000030C0-0x000030CF Standard Dual Channel PCI IDE Controller OK 
0x000001F0-0x000001F7 IDE Channel OK 
0x000003F6-0x000003F6 IDE Channel OK 
0x00000170-0x00000177 IDE Channel OK 
0x00000376-0x00000376 IDE Channel OK 
0x000030F0-0x000030F7 Standard Dual Channel PCI IDE Controller OK 
0x000030E4-0x000030E7 Standard Dual Channel PCI IDE Controller OK 
0x000030E8-0x000030EF Standard Dual Channel PCI IDE Controller OK 
0x000030E0-0x000030E3 Standard Dual Channel PCI IDE Controller OK 
0x000030D0-0x000030DF Standard Dual Channel PCI IDE Controller OK 
0x00004000-0x00004FFF PCI standard PCI-to-PCI bridge OK 
0x00004000-0x00004FFF NVIDIA GeForce 8200M G OK 
0x000003B0-0x000003BB PCI standard PCI-to-PCI bridge OK 
0x000003B0-0x000003BB NVIDIA GeForce 8200M G OK 
0x000003C0-0x000003DF PCI standard PCI-to-PCI bridge OK 
0x000003C0-0x000003DF NVIDIA GeForce 8200M G OK 
[IRQs]
Resource Device Status 
IRQ 81 Microsoft ACPI-Compliant System OK 
IRQ 82 Microsoft ACPI-Compliant System OK 
IRQ 83 Microsoft ACPI-Compliant System OK 
IRQ 84 Microsoft ACPI-Compliant System OK 
IRQ 85 Microsoft ACPI-Compliant System OK 
IRQ 86 Microsoft ACPI-Compliant System OK 
IRQ 87 Microsoft ACPI-Compliant System OK 
IRQ 88 Microsoft ACPI-Compliant System OK 
IRQ 89 Microsoft ACPI-Compliant System OK 
IRQ 90 Microsoft ACPI-Compliant System OK 
IRQ 91 Microsoft ACPI-Compliant System OK 
IRQ 92 Microsoft ACPI-Compliant System OK 
IRQ 93 Microsoft ACPI-Compliant System OK 
IRQ 94 Microsoft ACPI-Compliant System OK 
IRQ 95 Microsoft ACPI-Compliant System OK 
IRQ 96 Microsoft ACPI-Compliant System OK 
IRQ 97 Microsoft ACPI-Compliant System OK 
IRQ 98 Microsoft ACPI-Compliant System OK 
IRQ 99 Microsoft ACPI-Compliant System OK 
IRQ 100 Microsoft ACPI-Compliant System OK 
IRQ 101 Microsoft ACPI-Compliant System OK 
IRQ 102 Microsoft ACPI-Compliant System OK 
IRQ 103 Microsoft ACPI-Compliant System OK 
IRQ 104 Microsoft ACPI-Compliant System OK 
IRQ 105 Microsoft ACPI-Compliant System OK 
IRQ 106 Microsoft ACPI-Compliant System OK 
IRQ 107 Microsoft ACPI-Compliant System OK 
IRQ 108 Microsoft ACPI-Compliant System OK 
IRQ 109 Microsoft ACPI-Compliant System OK 
IRQ 110 Microsoft ACPI-Compliant System OK 
IRQ 111 Microsoft ACPI-Compliant System OK 
IRQ 112 Microsoft ACPI-Compliant System OK 
IRQ 113 Microsoft ACPI-Compliant System OK 
IRQ 114 Microsoft ACPI-Compliant System OK 
IRQ 115 Microsoft ACPI-Compliant System OK 
IRQ 116 Microsoft ACPI-Compliant System OK 
IRQ 117 Microsoft ACPI-Compliant System OK 
IRQ 118 Microsoft ACPI-Compliant System OK 
IRQ 119 Microsoft ACPI-Compliant System OK 
IRQ 120 Microsoft ACPI-Compliant System OK 
IRQ 121 Microsoft ACPI-Compliant System OK 
IRQ 122 Microsoft ACPI-Compliant System OK 
IRQ 123 Microsoft ACPI-Compliant System OK 
IRQ 124 Microsoft ACPI-Compliant System OK 
IRQ 125 Microsoft ACPI-Compliant System OK 
IRQ 126 Microsoft ACPI-Compliant System OK 
IRQ 127 Microsoft ACPI-Compliant System OK 
IRQ 128 Microsoft ACPI-Compliant System OK 
IRQ 129 Microsoft ACPI-Compliant System OK 
IRQ 130 Microsoft ACPI-Compliant System OK 
IRQ 131 Microsoft ACPI-Compliant System OK 
IRQ 132 Microsoft ACPI-Compliant System OK 
IRQ 133 Microsoft ACPI-Compliant System OK 
IRQ 134 Microsoft ACPI-Compliant System OK 
IRQ 135 Microsoft ACPI-Compliant System OK 
IRQ 136 Microsoft ACPI-Compliant System OK 
IRQ 137 Microsoft ACPI-Compliant System OK 
IRQ 138 Microsoft ACPI-Compliant System OK 
IRQ 139 Microsoft ACPI-Compliant System OK 
IRQ 140 Microsoft ACPI-Compliant System OK 
IRQ 141 Microsoft ACPI-Compliant System OK 
IRQ 142 Microsoft ACPI-Compliant System OK 
IRQ 143 Microsoft ACPI-Compliant System OK 
IRQ 144 Microsoft ACPI-Compliant System OK 
IRQ 145 Microsoft ACPI-Compliant System OK 
IRQ 146 Microsoft ACPI-Compliant System OK 
IRQ 147 Microsoft ACPI-Compliant System OK 
IRQ 148 Microsoft ACPI-Compliant System OK 
IRQ 149 Microsoft ACPI-Compliant System OK 
IRQ 150 Microsoft ACPI-Compliant System OK 
IRQ 151 Microsoft ACPI-Compliant System OK 
IRQ 152 Microsoft ACPI-Compliant System OK 
IRQ 153 Microsoft ACPI-Compliant System OK 
IRQ 154 Microsoft ACPI-Compliant System OK 
IRQ 155 Microsoft ACPI-Compliant System OK 
IRQ 156 Microsoft ACPI-Compliant System OK 
IRQ 157 Microsoft ACPI-Compliant System OK 
IRQ 158 Microsoft ACPI-Compliant System OK 
IRQ 159 Microsoft ACPI-Compliant System OK 
IRQ 160 Microsoft ACPI-Compliant System OK 
IRQ 161 Microsoft ACPI-Compliant System OK 
IRQ 162 Microsoft ACPI-Compliant System OK 
IRQ 163 Microsoft ACPI-Compliant System OK 
IRQ 164 Microsoft ACPI-Compliant System OK 
IRQ 165 Microsoft ACPI-Compliant System OK 
IRQ 166 Microsoft ACPI-Compliant System OK 
IRQ 167 Microsoft ACPI-Compliant System OK 
IRQ 168 Microsoft ACPI-Compliant System OK 
IRQ 169 Microsoft ACPI-Compliant System OK 
IRQ 170 Microsoft ACPI-Compliant System OK 
IRQ 171 Microsoft ACPI-Compliant System OK 
IRQ 172 Microsoft ACPI-Compliant System OK 
IRQ 173 Microsoft ACPI-Compliant System OK 
IRQ 174 Microsoft ACPI-Compliant System OK 
IRQ 175 Microsoft ACPI-Compliant System OK 
IRQ 176 Microsoft ACPI-Compliant System OK 
IRQ 177 Microsoft ACPI-Compliant System OK 
IRQ 178 Microsoft ACPI-Compliant System OK 
IRQ 179 Microsoft ACPI-Compliant System OK 
IRQ 180 Microsoft ACPI-Compliant System OK 
IRQ 181 Microsoft ACPI-Compliant System OK 
IRQ 182 Microsoft ACPI-Compliant System OK 
IRQ 183 Microsoft ACPI-Compliant System OK 
IRQ 184 Microsoft ACPI-Compliant System OK 
IRQ 185 Microsoft ACPI-Compliant System OK 
IRQ 186 Microsoft ACPI-Compliant System OK 
IRQ 187 Microsoft ACPI-Compliant System OK 
IRQ 188 Microsoft ACPI-Compliant System OK 
IRQ 189 Microsoft ACPI-Compliant System OK 
IRQ 190 Microsoft ACPI-Compliant System OK 
IRQ 13 Numeric data processor OK 
IRQ 1 Standard 101/102-Key or Microsoft Natural PS/2 Keyboard with HP QLB OK 
IRQ 12 Synaptics PS/2 Port TouchPad OK 
IRQ 10 NVIDIA nForce PCI System Management OK 
IRQ 18 NVIDIA nForce System Management Controller OK 
IRQ 17 Standard OpenHCD USB Host Controller OK 
IRQ 17 Standard Enhanced PCI to USB Host Controller OK 
IRQ 16 Standard OpenHCD USB Host Controller OK 
IRQ 16 Standard Enhanced PCI to USB Host Controller OK 
IRQ 14 IDE Channel OK 
IRQ 15 IDE Channel OK 
IRQ 20 High Definition Audio Controller OK 
IRQ 20 PCI standard PCI-to-PCI bridge OK 
IRQ 20 Atheros AR5007 802.11b/g WiFi Adapter OK 
IRQ 21 Standard Dual Channel PCI IDE Controller OK 
IRQ 4294967294 NVIDIA nForce 10/100/1000 Mbps Networking Controller OK 
IRQ 23 NVIDIA GeForce 8200M G OK 
IRQ 0 High precision event timer OK 
IRQ 8 High precision event timer OK 
[Memory]
Resource Device Status 
0xA0000-0xBFFFF PCI bus OK 
0xA0000-0xBFFFF PCI standard PCI-to-PCI bridge OK 
0xA0000-0xBFFFF NVIDIA GeForce 8200M G OK 
0xC0000-0xC3FFF PCI bus OK 
0xC4000-0xC7FFF PCI bus OK 
0xC8000-0xCBFFF PCI bus OK 
0xCC000-0xCFFFF PCI bus OK 
0xD0000-0xD3FFF PCI bus OK 
0xD4000-0xD7FFF PCI bus OK 
0xD8000-0xDBFFF PCI bus OK 
0xDC000-0xDFFFF PCI bus OK 
0xE0000-0xE3FFF PCI bus OK 
0xE4000-0xE7FFF PCI bus OK 
0xE8000-0xEBFFF PCI bus OK 
0xEC000-0xEFFFF PCI bus OK 
0xF0000-0xFFFFF PCI bus OK 
0x80000000-0xFEBFFFFF PCI bus OK 
0xE0000000-0xEFFFFFFF Motherboard resources OK 
0xFF800000-0xFF800FFF Motherboard resources OK 
0xC0080000-0xC00FFFFF NVIDIA nForce System Management Controller OK 
0xC0006000-0xC0006FFF Standard OpenHCD USB Host Controller OK 
0xC0007000-0xC00070FF Standard Enhanced PCI to USB Host Controller OK 
0xC0008000-0xC0008FFF Standard OpenHCD USB Host Controller OK 
0xC0007400-0xC00074FF Standard Enhanced PCI to USB Host Controller OK 
0xC0000000-0xC0003FFF High Definition Audio Controller OK 
0xC0004000-0xC0005FFF Standard Dual Channel PCI IDE Controller OK 
0xC0009000-0xC0009FFF NVIDIA nForce 10/100/1000 Mbps Networking Controller OK 
0xC0007C00-0xC0007CFF NVIDIA nForce 10/100/1000 Mbps Networking Controller OK 
0xC0007800-0xC000780F NVIDIA nForce 10/100/1000 Mbps Networking Controller OK 
0xC1000000-0xC1FFFFFF PCI standard PCI-to-PCI bridge OK 
0xC1000000-0xC1FFFFFF NVIDIA GeForce 8200M G OK 
0xC4000000-0xDFFFFFFF PCI standard PCI-to-PCI bridge OK 
0xC4000000-0xDFFFFFFF NVIDIA GeForce 8200M G OK 
0xD0000000-0xDFFFFFFF NVIDIA GeForce 8200M G OK 
0xC2000000-0xC20FFFFF PCI standard PCI-to-PCI bridge OK 
0xC2000000-0xC20FFFFF Atheros AR5007 802.11b/g WiFi Adapter OK 
0xFED00000-0xFED003FF High precision event timer OK 
0xFED00000-0xFED003FF System board OK 
0xFFC00000-0xFFFFFFFF System board OK 
0xFEC00000-0xFEC00FFF System board OK 
0xFEE00000-0xFEEFFFFF System board OK 
0xFEF00000-0xFEF00FFF System board OK 
[Components]
 
[Multimedia]
 
[Audio Codecs]
CODEC Manufacturer Description Status File Version Size Creation Date 
c:\windows\system32\msg711.acm Microsoft Corporation OK C:\Windows\system32\MSG711.ACM 6.0.6000.16386 12.00 KB (12,288 bytes) 11/2/2006 5:03 AM 
c:\windows\system32\imaadp32.acm Microsoft Corporation OK C:\Windows\system32\IMAADP32.ACM 6.0.6000.16386 17.00 KB (17,408 bytes) 11/2/2006 5:03 AM 
c:\windows\system32\msgsm32.acm Microsoft Corporation OK C:\Windows\system32\MSGSM32.ACM 6.0.6000.16386 22.50 KB (23,040 bytes) 11/2/2006 5:03 AM 
c:\windows\system32\msadp32.acm Microsoft Corporation OK C:\Windows\system32\MSADP32.ACM 6.0.6000.16386 17.00 KB (17,408 bytes) 11/2/2006 5:03 AM 
c:\windows\system32\l3codecp.acm Fraunhofer Institut Integrierte Schaltungen IIS OK C:\Windows\system32\L3CODECP.ACM 3.4.0.0 215.50 KB (220,672 bytes) 1/20/2008 9:25 PM 
c:\windows\system32\l3codeca.acm Fraunhofer Institut Integrierte Schaltungen IIS Fraunhofer IIS MPEG Layer-3 Codec OK C:\Windows\system32\L3CODECA.ACM 1.9.0.401 61.00 KB (62,464 bytes) 1/20/2008 9:25 PM 
[Video Codecs]
CODEC Manufacturer Description Status File Version Size Creation Date 
c:\windows\system32\msrle32.dll Microsoft Corporation OK C:\Windows\system32\MSRLE32.DLL 6.0.6000.16386 12.50 KB (12,800 bytes) 11/2/2006 5:03 AM 
c:\windows\system32\msvidc32.dll Microsoft Corporation OK C:\Windows\system32\MSVIDC32.DLL 6.0.6001.18000 30.50 KB (31,232 bytes) 1/20/2008 9:24 PM 
c:\windows\system32\iccvid.dll Radius Inc. OK C:\Windows\system32\ICCVID.DLL 1.10.0.12 80.00 KB (81,920 bytes) 11/2/2006 8:34 AM 
c:\windows\system32\tsbyuv.dll Microsoft Corporation OK C:\Windows\system32\TSBYUV.DLL 6.0.6002.18005 12.00 KB (12,288 bytes) 1/3/2010 3:54 PM 
c:\windows\system32\iyuv_32.dll Microsoft Corporation OK C:\Windows\system32\IYUV_32.DLL 6.0.6000.16386 48.50 KB (49,664 bytes) 11/2/2006 4:55 AM 
c:\windows\system32\msyuv.dll Microsoft Corporation OK C:\Windows\system32\MSYUV.DLL 6.0.6000.16386 22.00 KB (22,528 bytes) 11/2/2006 4:55 AM 
[CD-ROM]
Item Value 
Drive E: 
Description CD-ROM Drive 
Media Loaded No 
Media Type UNKNOWN 
Name Optiarc DVD RW AD-7580S ATA Device 
Manufacturer (Standard CD-ROM drives) 
Status OK 
Transfer Rate -1.00 kbytes/sec 
SCSI Target ID 0 
PNP Device ID IDE\CDROMOPTIARC_DVD_RW_AD-7580S_________________FH03____\5&1BA4DB8C&0&0.0.0 
Driver c:\windows\system32\drivers\cdrom.sys (6.0.6002.18005, 65.50 KB (67,072 bytes), 1/3/2010 3:53 PM) 
[Sound Device]
Item Value 
Name Conexant High Definition SmartAudio 221 
Manufacturer Conexant 
Status OK 
PNP Device ID HDAUDIO\FUNC_01&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0001 
Driver c:\windows\system32\drivers\chdrt32.sys (4.58.0.0, 217.00 KB (222,208 bytes), 6/5/2008 12:58 PM) 
 
Name NVIDIA HDMI Audio 
Manufacturer NVIDIA 
Status OK 
PNP Device ID HDAUDIO\FUNC_01&VEN_10DE&DEV_0002&SUBSYS_10DE0101&REV_1000\4&7CC389&0&0301 
Driver c:\windows\system32\drivers\nvhda32v.sys (1.0.0.27, 42.03 KB (43,040 bytes), 5/9/2008 3:17 PM) 
[Display]
Item Value 
Name NVIDIA GeForce 8200M G 
PNP Device ID PCI\VEN_10DE&DEV_0845&SUBSYS_360A103C&REV_A2\4&105D929E&0&0058 
Adapter Type GeForce 8200M G, NVIDIA compatible 
Adapter Description NVIDIA GeForce 8200M G 
Adapter RAM 256.00 MB (268,435,456 bytes) 
Installed Drivers nvd3dum.dll,nvwgf2um.dll 
Driver Version 7.15.11.7614 
INF File oem8.inf (nv_C77 section) 
Color Planes Not Available 
Color Table Entries 4294967296 
Resolution 1366 x 768 x 60 hertz 
Bits/Pixel 32 
Memory Address 0xC1000000-0xC1FFFFFF 
Memory Address 0xD0000000-0xDFFFFFFF 
Memory Address 0xC4000000-0xDFFFFFFF 
I/O Port 0x00004000-0x00004FFF 
IRQ Channel IRQ 23 
I/O Port 0x000003B0-0x000003BB 
I/O Port 0x000003C0-0x000003DF 
Memory Address 0xA0000-0xBFFFF 
Driver c:\windows\system32\drivers\nvlddmkm.sys (7.15.11.7614, 7.18 MB (7,530,656 bytes), 7/11/2008 2:31 PM) 
[Infrared]
Item Value 
[Input]
 
[Keyboard]
Item Value 
Description Standard 101/102-Key or Microsoft Natural PS/2 Keyboard with HP QLB 
Name Enhanced (101- or 102-key) 
Layout 00000409 
PNP Device ID ACPI\PNP0303\4&86EF4A8&0 
Number of Function Keys 12 
I/O Port 0x00000060-0x00000060 
I/O Port 0x00000064-0x00000064 
IRQ Channel IRQ 1 
Driver c:\windows\system32\drivers\i8042prt.sys (6.0.6001.18000, 53.50 KB (54,784 bytes), 1/20/2008 9:23 PM) 
[Pointing Device]
Item Value 
Hardware Type Synaptics PS/2 Port TouchPad 
Number of Buttons 0 
Status OK 
PNP Device ID ACPI\SYN0158\4&86EF4A8&0 
Power Management Supported No 
Double Click Threshold Not Available 
Handedness Not Available 
IRQ Channel IRQ 12 
Driver c:\windows\system32\drivers\i8042prt.sys (6.0.6001.18000, 53.50 KB (54,784 bytes), 1/20/2008 9:23 PM) 
[Modem]
Item Value 
Name HDAUDIO Soft Data Fax Modem with SmartCP 
Description HDAUDIO Soft Data Fax Modem with SmartCP 
Device ID HDAUDIO\FUNC_02&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0002 
Device Type Internal Modem 
Attached To COM3 
Answer Mode Not Available 
PNP Device ID HDAUDIO\FUNC_02&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0002 
Provider Name CXT 
Modem INF Path oem10.inf 
Modem INF Section ModemX 
Blind Off X4 
Blind On X3 
Compression Off +DS=0;+DS44=0; 
Compression On +DS=3;+DS44=3; 
Error Control Forced +ES=3,2,4; 
Error Control Off +ES=1,0,1; 
Error Control On +ES=3,0,2; 
Flow Control Hard +IFC=2,2; 
Flow Control Off +IFC=0,0; 
Flow Control Soft +IFC=1,1; 
DCB &#x001c; 
Default < 
Inactivity Timeout 0 
Modulation Bell Not Available 
Modulation CCITT Not Available 
Prefix AT 
Pulse P 
Reset ATZ<cr> 
Responses Key Name HDAUDIO Soft Data Fax Modem with SmartCP::CXT::CXT 
Speaker Mode Dial M1 
Speaker Mode Off M0 
Speaker Mode On M2 
Speaker Mode Setup M3 
Speaker Volume High L3 
Speaker Volume Low L1 
Speaker Volume Med L2 
String Format Not Available 
Terminator <cr> 
Tone T 
Driver c:\windows\system32\drivers\modem.sys (6.0.6001.18000, 31.00 KB (31,744 bytes), 1/20/2008 9:24 PM) 
[Network]
 
[Adapter]
Item Value 
Name [00000000] WAN Miniport (L2TP) 
Adapter Type Not Available 
Product Type WAN Miniport (L2TP) 
Installed Yes 
PNP Device ID ROOT\MS_L2TPMINIPORT\0000 
Last Reset 1/3/2010 5:14 PM 
Index 0 
Service Name Rasl2tp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\rasl2tp.sys (6.0.6001.18000, 74.50 KB (76,288 bytes), 1/20/2008 9:24 PM) 
 
Name [00000001] WAN Miniport (PPTP) 
Adapter Type Wide Area Network (WAN) 
Product Type WAN Miniport (PPTP) 
Installed Yes 
PNP Device ID ROOT\MS_PPTPMINIPORT\0000 
Last Reset 1/3/2010 5:14 PM 
Index 1 
Service Name PptpMiniport 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 50:50:54:50:30:30 
Driver c:\windows\system32\drivers\raspptp.sys (6.0.6001.18000, 61.50 KB (62,976 bytes), 1/20/2008 9:24 PM) 
 
Name [00000002] WAN Miniport (PPPOE) 
Adapter Type Wide Area Network (WAN) 
Product Type WAN Miniport (PPPOE) 
Installed Yes 
PNP Device ID ROOT\MS_PPPOEMINIPORT\0000 
Last Reset 1/3/2010 5:14 PM 
Index 2 
Service Name RasPppoe 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 33:50:6F:45:30:30 
Driver c:\windows\system32\drivers\raspppoe.sys (6.0.6002.18005, 40.50 KB (41,472 bytes), 1/3/2010 3:55 PM) 
 
Name [00000003] WAN Miniport (IPv6) 
Adapter Type Not Available 
Product Type WAN Miniport (IPv6) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANIPV6\0000 
Last Reset 1/3/2010 5:14 PM 
Index 3 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6002.18005, 118.50 KB (121,344 bytes), 1/3/2010 3:55 PM) 
 
Name [00000004] Atheros AR5007 802.11b/g WiFi Adapter 
Adapter Type Ethernet 802.3 
Product Type Atheros AR5007 802.11b/g WiFi Adapter 
Installed Yes 
PNP Device ID PCI\VEN_168C&DEV_001C&SUBSYS_137A103C&REV_01\4&B224E5E&0&00A0 
Last Reset 1/3/2010 5:14 PM 
Index 4 
Service Name athr 
IP Address 192.168.2.5, fe80::85d3:7ca2:8629:e7d0 
IP Subnet 255.255.255.0, 64 
Default IP Gateway 192.168.2.1 
DHCP Enabled Yes 
DHCP Server 192.168.2.1 
DHCP Lease Expires 1/18/2038 10:14 PM 
DHCP Lease Obtained 1/3/2010 6:18 PM 
MAC Address 00:24:2B:95:56:BD 
Memory Address 0xC2000000-0xC20FFFFF 
IRQ Channel IRQ 20 
Driver c:\windows\system32\drivers\athr.sys (7.6.0.114, 888.50 KB (909,824 bytes), 1/3/2010 5:38 PM) 
 
Name [00000006] WAN Miniport (IP) 
Adapter Type Not Available 
Product Type WAN Miniport (IP) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANIP\0000 
Last Reset 1/3/2010 5:14 PM 
Index 6 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6002.18005, 118.50 KB (121,344 bytes), 1/3/2010 3:55 PM) 
 
Name [00000007] NVIDIA nForce Networking Controller 
Adapter Type Ethernet 802.3 
Product Type NVIDIA nForce Networking Controller 
Installed Yes 
PNP Device ID PCI\VEN_10DE&DEV_0760&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&50 
Last Reset 1/3/2010 5:14 PM 
Index 7 
Service Name NVENETFD 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled Yes 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 00:1F:16:70:79:7F 
Memory Address 0xC0009000-0xC0009FFF 
Memory Address 0xC0007C00-0xC0007CFF 
Memory Address 0xC0007800-0xC000780F 
IRQ Channel IRQ 4294967294 
Driver c:\windows\system32\drivers\nvmfdx32.sys (1.0.1.6776, 1,018.03 KB (1,042,464 bytes), 1/29/2008 8:55 AM) 
 
Name [00000009] RAS Async Adapter 
Adapter Type Not Available 
Product Type RAS Async Adapter 
Installed Yes 
PNP Device ID Not Available 
Last Reset 1/3/2010 5:14 PM 
Index 9 
Service Name AsyncMac 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
 
Name [00000010] WAN Miniport (SSTP) 
Adapter Type Not Available 
Product Type WAN Miniport (SSTP) 
Installed Yes 
PNP Device ID ROOT\MS_SSTPMINIPORT\0000 
Last Reset 1/3/2010 5:14 PM 
Index 10 
Service Name RasSstp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\rassstp.sys (6.0.6002.18005, 67.50 KB (69,120 bytes), 1/3/2010 3:55 PM) 
 
Name [00000011] WAN Miniport (Network Monitor) 
Adapter Type Not Available 
Product Type WAN Miniport (Network Monitor) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANBH\0000 
Last Reset 1/3/2010 5:14 PM 
Index 11 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6002.18005, 118.50 KB (121,344 bytes), 1/3/2010 3:55 PM) 
 
Name [00000012] Microsoft Tun Miniport Adapter 
Adapter Type Ethernet 802.3 
Product Type Microsoft Tun Miniport Adapter 
Installed Yes 
PNP Device ID ROOT\*TUNMP\0000 
Last Reset 1/3/2010 5:14 PM 
Index 12 
Service Name tunmp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 02:00:54:55:4E:01 
Driver c:\windows\system32\drivers\tunmp.sys (6.0.6001.18000, 15.00 KB (15,360 bytes), 1/20/2008 9:24 PM) 
 
Name [00000013] Microsoft ISATAP Adapter 
Adapter Type Tunnel 
Product Type Microsoft ISATAP Adapter 
Installed Yes 
PNP Device ID ROOT\*ISATAP\0002 
Last Reset 1/3/2010 5:14 PM 
Index 13 
Service Name tunnel 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\tunnel.sys (6.0.6001.18000, 22.50 KB (23,040 bytes), 1/20/2008 9:24 PM) 
[Protocol]
Item Value 
Name MSAFD Tcpip [TCP/IP] 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 16 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD Tcpip [UDP/IP] 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 16 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name MSAFD Tcpip [TCP/IPv6] 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 28 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD Tcpip [UDP/IPv6] 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 28 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name RSVP TCPv6 Service Provider 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 28 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name RSVP TCP Service Provider 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 16 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name RSVP UDPv6 Service Provider 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 28 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name RSVP UDP Service Provider 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 16 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip_{7C3D2452-AFCE-43F8-9D2D-452EA6C31ECB}] SEQPACKET 3 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip_{7C3D2452-AFCE-43F8-9D2D-452EA6C31ECB}] DATAGRAM 3 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip_{F8E7AB6D-163F-4FBB-80ED-B161735E52C0}] SEQPACKET 1 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip_{F8E7AB6D-163F-4FBB-80ED-B161735E52C0}] DATAGRAM 1 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{0EB3005E-490E-446A-8376-54C6CFBA09B4}] SEQPACKET 7 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{0EB3005E-490E-446A-8376-54C6CFBA09B4}] DATAGRAM 7 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{51A7FE3A-06A3-4C63-87A4-3002D59D4AC4}] SEQPACKET 6 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{51A7FE3A-06A3-4C63-87A4-3002D59D4AC4}] DATAGRAM 6 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{7C3D2452-AFCE-43F8-9D2D-452EA6C31ECB}] SEQPACKET 4 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{7C3D2452-AFCE-43F8-9D2D-452EA6C31ECB}] DATAGRAM 4 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{F8E7AB6D-163F-4FBB-80ED-B161735E52C0}] SEQPACKET 2 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD NetBIOS [\Device\NetBT_Tcpip6_{F8E7AB6D-163F-4FBB-80ED-B161735E52C0}] DATAGRAM 2 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 20 bytes 
Maximum Message Size 62.50 KB (64,000 bytes) 
Message Oriented Yes 
Minimum Address Size 20 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
[WinSock]
Item Value 
File c:\windows\system32\winsock.dll 
Size 2.80 KB (2,864 bytes) 
Version 3.10.0.103 
 
File c:\windows\system32\wsock32.dll 
Size 15.00 KB (15,360 bytes) 
Version 6.0.6001.18000 
[Ports]
 
[Serial]
Item Value 
Name HDAUDIO Soft Data Fax Modem with SmartCP 
Status OK 
PNP Device ID HDAUDIO\FUNC_02&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0002 
Maximum Input Buffer Size 0 
Maximum Output Buffer Size No 
Settable Baud Rate Yes 
Settable Data Bits Yes 
Settable Flow Control Yes 
Settable Parity Yes 
Settable Parity Check Yes 
Settable Stop Bits Yes 
Settable RLSD Yes 
Supports RLSD Yes 
Supports 16 Bit Mode No 
Supports Special Characters No 
Baud Rate 9600 
Bits/Byte 8 
Stop Bits 1 
Parity None 
Busy No 
Abort Read/Write on Error No 
Binary Mode Enabled Yes 
Continue XMit on XOff No 
CTS Outflow Control No 
Discard NULL Bytes No 
DSR Outflow Control 0 
DSR Sensitivity 0 
DTR Flow Control Type Disable 
EOF Character 0 
Error Replace Character 0 
Error Replacement Enabled No 
Event Character 0 
Parity Check Enabled No 
RTS Flow Control Type Disable 
XOff Character 0 
XOffXMit Threshold 0 
XOn Character 0 
XOnXMit Threshold 0 
XOnXOff InFlow Control 0 
XOnXOff OutFlow Control 0 
Driver c:\windows\system32\drivers\modem.sys (6.0.6001.18000, 31.00 KB (31,744 bytes), 1/20/2008 9:24 PM) 
[Parallel]
Item Value 
[Storage]
 
[Drives]
Item Value 
Drive C: 
Description Local Fixed Disk 
Compressed No 
File System NTFS 
Size 124.04 GB (133,183,696,896 bytes) 
Free Space 88.61 GB (95,142,899,712 bytes) 
Volume Name 
Volume Serial Number F4EEF6D4 
 
Drive D: 
Description Local Fixed Disk 
Compressed Not Available 
File System Not Available 
Size Not Available 
Free Space Not Available 
Volume Name Not Available 
Volume Serial Number Not Available 
 
Drive E: 
Description CD-ROM Disc 
[Disks]
Item Value 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model SAMSUNG HM251JI ATA Device 
Bytes/Sector 512 
Media Loaded Yes 
Media Type Fixed hard disk 
Partitions 4 
SCSI Bus 1 
SCSI Logical Unit 0 
SCSI Port 3 
SCSI Target ID 0 
Sectors/Track 63 
Size 232.88 GB (250,056,737,280 bytes) 
Total Cylinders 30,401 
Total Sectors 488,392,065 
Total Tracks 7,752,255 
Tracks/Cylinder 255 
Partition Disk #0, Partition #0 
Partition Size 124.04 GB (133,183,701,504 bytes) 
Partition Starting Offset 32,256 bytes 
Partition Disk #0, Partition #1 
Partition Size 10.88 GB (11,679,897,600 bytes) 
Partition Starting Offset 238,376,839,680 bytes 
Partition Disk #0, Partition #2 
Partition Size 97.97 GB (105,193,105,920 bytes) 
Partition Starting Offset 133,183,733,760 bytes 
[SCSI]
Item Value 
Name Microsoft iSCSI Initiator 
Manufacturer Microsoft 
Status OK 
PNP Device ID ROOT\ISCSIPRT\0000 
Driver c:\windows\system32\drivers\msiscsi.sys (6.0.6002.18005, 176.48 KB (180,712 bytes), 1/3/2010 3:53 PM) 
[IDE]
Item Value 
Name Standard Dual Channel PCI IDE Controller 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCI\VEN_10DE&DEV_0759&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&30 
I/O Port 0x000030C0-0x000030CF 
Driver c:\windows\system32\drivers\pciide.sys (6.0.6002.18005, 13.98 KB (14,312 bytes), 1/3/2010 3:56 PM) 
 
Name IDE Channel 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCIIDE\IDECHANNEL\4&12D80BB5&0&0 
I/O Port 0x000001F0-0x000001F7 
I/O Port 0x000003F6-0x000003F6 
IRQ Channel IRQ 14 
Driver c:\windows\system32\drivers\atapi.sys (6.0.6002.18005, 19.48 KB (19,944 bytes), 1/3/2010 3:56 PM) 
 
Name IDE Channel 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCIIDE\IDECHANNEL\4&12D80BB5&0&1 
I/O Port 0x00000170-0x00000177 
I/O Port 0x00000376-0x00000376 
IRQ Channel IRQ 15 
Driver c:\windows\system32\drivers\atapi.sys (6.0.6002.18005, 19.48 KB (19,944 bytes), 1/3/2010 3:56 PM) 
 
Name Standard Dual Channel PCI IDE Controller 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCI\VEN_10DE&DEV_0AD0&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&48 
I/O Port 0x000030F0-0x000030F7 
I/O Port 0x000030E4-0x000030E7 
I/O Port 0x000030E8-0x000030EF 
I/O Port 0x000030E0-0x000030E3 
I/O Port 0x000030D0-0x000030DF 
Memory Address 0xC0004000-0xC0005FFF 
IRQ Channel IRQ 21 
Driver c:\windows\system32\drivers\pciide.sys (6.0.6002.18005, 13.98 KB (14,312 bytes), 1/3/2010 3:56 PM) 
 
Name IDE Channel 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCIIDE\IDECHANNEL\4&26AC2C3E&0&0 
Driver c:\windows\system32\drivers\atapi.sys (6.0.6002.18005, 19.48 KB (19,944 bytes), 1/3/2010 3:56 PM) 
 
Name IDE Channel 
Manufacturer (Standard IDE ATA/ATAPI controllers) 
Status OK 
PNP Device ID PCIIDE\IDECHANNEL\4&26AC2C3E&0&1 
Driver c:\windows\system32\drivers\atapi.sys (6.0.6002.18005, 19.48 KB (19,944 bytes), 1/3/2010 3:56 PM) 
[Printing]
Name Driver Port Name Server Name 
Microsoft XPS Document Writer Microsoft XPS Document Writer XPSPort: 
[Problem Devices]
Device PNP Device ID Error Code 
[USB]
Device PNP Device ID 
Standard OpenHCD USB Host Controller PCI\VEN_10DE&DEV_077B&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&10 
Standard Enhanced PCI to USB Host Controller PCI\VEN_10DE&DEV_077C&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&11 
Standard OpenHCD USB Host Controller PCI\VEN_10DE&DEV_077D&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&20 
Standard Enhanced PCI to USB Host Controller PCI\VEN_10DE&DEV_077E&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&21 
[Software Environment]
 
[System Drivers]
Name Description File Type Started Start Mode State Status Error Control Accept Pause Accept Stop 
acpi Microsoft ACPI Driver c:\windows\system32\drivers\acpi.sys Kernel Driver Yes Boot Running OK Critical No Yes 
adp94xx adp94xx c:\windows\system32\drivers\adp94xx.sys Kernel Driver Yes Boot Running OK Normal No Yes 
adpahci adpahci c:\windows\system32\drivers\adpahci.sys Kernel Driver Yes Boot Running OK Normal No Yes 
adpu160m adpu160m c:\windows\system32\drivers\adpu160m.sys Kernel Driver Yes Boot Running OK Normal No Yes 
adpu320 adpu320 c:\windows\system32\drivers\adpu320.sys Kernel Driver Yes Boot Running OK Normal No Yes 
afd Ancilliary Function Driver for Winsock c:\windows\system32\drivers\afd.sys Kernel Driver Yes System Running OK Normal No Yes 
agp440 Intel AGP Bus Filter c:\windows\system32\drivers\agp440.sys Kernel Driver No Manual Stopped OK Normal No No 
aic78xx aic78xx c:\windows\system32\drivers\djsvs.sys Kernel Driver Yes Boot Running OK Normal No Yes 
aliide aliide c:\windows\system32\drivers\aliide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
amdagp AMD AGP Bus Filter Driver c:\windows\system32\drivers\amdagp.sys Kernel Driver No Manual Stopped OK Normal No No 
amdide amdide c:\windows\system32\drivers\amdide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
amdk7 AMD K7 Processor Driver c:\windows\system32\drivers\amdk7.sys Kernel Driver No Manual Stopped OK Normal No No 
amdk8 AMD K8 Processor Driver c:\windows\system32\drivers\amdk8.sys Kernel Driver No Manual Stopped OK Normal No No 
arc arc c:\windows\system32\drivers\arc.sys Kernel Driver Yes Boot Running OK Normal No Yes 
arcsas arcsas c:\windows\system32\drivers\arcsas.sys Kernel Driver Yes Boot Running OK Normal No Yes 
asyncmac RAS Asynchronous Media Driver c:\windows\system32\drivers\asyncmac.sys Kernel Driver No Manual Stopped OK Normal No No 
atapi IDE Channel c:\windows\system32\drivers\atapi.sys Kernel Driver Yes Boot Running OK Critical No Yes 
athr Atheros Extensible Wireless LAN device driver c:\windows\system32\drivers\athr.sys Kernel Driver Yes Manual Running OK Normal No Yes 
beep Beep c:\windows\system32\drivers\beep.sys Kernel Driver Yes System Running OK Normal No Yes 
blbdrive blbdrive c:\windows\system32\drivers\blbdrive.sys Kernel Driver No Manual Stopped OK Normal No No 
bowser Bowser c:\windows\system32\drivers\bowser.sys File System Driver Yes Manual Running OK Normal No Yes 
brfiltlo Brother USB Mass-Storage Lower Filter Driver c:\windows\system32\drivers\brfiltlo.sys Kernel Driver No Manual Stopped OK Normal No No 
brfiltup Brother USB Mass-Storage Upper Filter Driver c:\windows\system32\drivers\brfiltup.sys Kernel Driver No Manual Stopped OK Normal No No 
brserid Brother MFC Serial Port Interface Driver (WDM) c:\windows\system32\drivers\brserid.sys Kernel Driver No Manual Stopped OK Normal No No 
brserwdm Brother WDM Serial driver c:\windows\system32\drivers\brserwdm.sys Kernel Driver No Manual Stopped OK Normal No No 
brusbmdm Brother MFC USB Fax Only Modem c:\windows\system32\drivers\brusbmdm.sys Kernel Driver No Manual Stopped OK Normal No No 
brusbser Brother MFC USB Serial WDM Driver c:\windows\system32\drivers\brusbser.sys Kernel Driver No Manual Stopped OK Normal No No 
bthmodem Bluetooth Serial Communications Driver c:\windows\system32\drivers\bthmodem.sys Kernel Driver No Manual Stopped OK Normal No No 
cdfs CD/DVD File System Reader c:\windows\system32\drivers\cdfs.sys File System Driver Yes Disabled Running OK Normal No Yes 
cdrom CD-ROM Driver c:\windows\system32\drivers\cdrom.sys Kernel Driver Yes System Running OK Normal No Yes 
circlass Consumer IR Devices c:\windows\system32\drivers\circlass.sys Kernel Driver No Manual Stopped OK Normal No No 
clfs Common Log (CLFS) c:\windows\system32\clfs.sys Kernel Driver Yes Boot Running OK Critical No Yes 
cmbatt Microsoft ACPI Control Method Battery Driver c:\windows\system32\drivers\cmbatt.sys Kernel Driver Yes Manual Running OK Normal No Yes 
cmdide cmdide c:\windows\system32\drivers\cmdide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
cnxthdaudservice Conexant UAA Function Driver for High Definition Audio Service c:\windows\system32\drivers\chdrt32.sys Kernel Driver Yes Manual Running OK Normal No Yes 
compbatt Microsoft Composite Battery Driver c:\windows\system32\drivers\compbatt.sys Kernel Driver Yes Boot Running OK Critical No Yes 
crcdisk Crcdisk Filter Driver c:\windows\system32\drivers\crcdisk.sys Kernel Driver Yes Boot Running OK Normal No Yes 
crusoe Transmeta Crusoe Processor Driver c:\windows\system32\drivers\crusoe.sys Kernel Driver No Manual Stopped OK Normal No No 
dfsc DFS Namespace Client Driver c:\windows\system32\drivers\dfsc.sys File System Driver Yes System Running OK Normal No Yes 
disk Disk Driver c:\windows\system32\drivers\disk.sys Kernel Driver Yes Boot Running OK Normal No Yes 
drmkaud Microsoft Kernel DRM Audio Descrambler c:\windows\system32\drivers\drmkaud.sys Kernel Driver No Manual Stopped OK Normal No No 
dxgkrnl LDDM Graphics Subsystem c:\windows\system32\drivers\dxgkrnl.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
e1g60 Intel(R) PRO/1000 NDIS 6 Adapter Driver c:\windows\system32\drivers\e1g60i32.sys Kernel Driver No Manual Stopped OK Normal No No 
ecache ReadyBoost Caching Driver c:\windows\system32\drivers\ecache.sys Kernel Driver Yes Boot Running OK Critical No Yes 
elxstor elxstor c:\windows\system32\drivers\elxstor.sys Kernel Driver Yes Boot Running OK Normal No Yes 
errdev Microsoft Hardware Error Device Driver c:\windows\system32\drivers\errdev.sys Kernel Driver No Manual Stopped OK Normal No No 
exfat exFAT File System Driver c:\windows\system32\drivers\exfat.sys File System Driver No Manual Stopped OK Normal No No 
fastfat FAT12/16/32 File System Driver c:\windows\system32\drivers\fastfat.sys File System Driver No Manual Stopped OK Normal No No 
fdc Floppy Disk Controller Driver c:\windows\system32\drivers\fdc.sys Kernel Driver No Manual Stopped OK Normal No No 
fileinfo File Information FS MiniFilter c:\windows\system32\drivers\fileinfo.sys File System Driver Yes Boot Running OK Normal No Yes 
filetrace FileTrace c:\windows\system32\drivers\filetrace.sys File System Driver No Manual Stopped OK Normal No No 
flpydisk Floppy Disk Driver c:\windows\system32\drivers\flpydisk.sys Kernel Driver No Manual Stopped OK Normal No No 
fltmgr FltMgr c:\windows\system32\drivers\fltmgr.sys File System Driver Yes Boot Running OK Critical No Yes 
gagp30kx Microsoft Generic AGPv3.0 Filter for K8 Processor Platforms c:\windows\system32\drivers\gagp30kx.sys Kernel Driver No Manual Stopped OK Normal No No 
hdaudaddservice Microsoft 1.1 UAA Function Driver for High Definition Audio Service c:\windows\system32\drivers\hdaudio.sys Kernel Driver No Manual Stopped OK Normal No No 
hdaudbus Microsoft UAA Bus Driver for High Definition Audio c:\windows\system32\drivers\hdaudbus.sys Kernel Driver Yes Manual Running OK Normal No Yes 
hidbth Microsoft Bluetooth HID Miniport c:\windows\system32\drivers\hidbth.sys Kernel Driver No Manual Stopped OK Ignore No No 
hidir Microsoft Infrared HID Driver c:\windows\system32\drivers\hidir.sys Kernel Driver No Manual Stopped OK Ignore No No 
hidusb Microsoft HID Class Driver c:\windows\system32\drivers\hidusb.sys Kernel Driver No Manual Stopped OK Ignore No No 
hpcisss HpCISSs c:\windows\system32\drivers\hpcisss.sys Kernel Driver Yes Boot Running OK Normal No Yes 
hpqkbfiltr HpqKbFilter Driver c:\windows\system32\drivers\hpqkbfiltr.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
hsf_dpv HSF_DPV c:\windows\system32\drivers\hsx_dpv.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
hsxhwazl HSXHWAZL c:\windows\system32\drivers\hsxhwazl.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
http HTTP c:\windows\system32\drivers\http.sys Kernel Driver Yes Manual Running OK Normal No Yes 
i2omp i2omp c:\windows\system32\drivers\i2omp.sys Kernel Driver Yes Boot Running OK Normal No Yes 
i8042prt i8042 Keyboard and PS/2 Mouse Port Driver c:\windows\system32\drivers\i8042prt.sys Kernel Driver Yes System Running OK Normal No Yes 
iastorv Intel RAID Controller Vista c:\windows\system32\drivers\iastorv.sys Kernel Driver Yes Boot Running OK Normal No Yes 
iirsp iirsp c:\windows\system32\drivers\iirsp.sys Kernel Driver Yes Boot Running OK Normal No Yes 
intelide intelide c:\windows\system32\drivers\intelide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
intelppm Intel Processor Driver c:\windows\system32\drivers\intelppm.sys Kernel Driver No Manual Stopped OK Normal No No 
ipfilterdriver IP Traffic Filter Driver c:\windows\system32\drivers\ipfltdrv.sys Kernel Driver No Manual Stopped OK Normal No No 
ipmidrv IPMIDRV c:\windows\system32\drivers\ipmidrv.sys Kernel Driver No Manual Stopped OK Normal No No 
ipnat IP Network Address Translator c:\windows\system32\drivers\ipnat.sys Kernel Driver No Manual Stopped OK Normal No No 
irenum IR Bus Enumerator c:\windows\system32\drivers\irenum.sys Kernel Driver No Manual Stopped OK Ignore No No 
isapnp PnP ISA/EISA Bus Driver c:\windows\system32\drivers\isapnp.sys Kernel Driver Yes Boot Running OK Critical No Yes 
iscsiprt iScsiPort Driver c:\windows\system32\drivers\msiscsi.sys Kernel Driver Yes Manual Running OK Normal No Yes 
iteatapi ITEATAPI_Service_Install c:\windows\system32\drivers\iteatapi.sys Kernel Driver Yes Boot Running OK Normal No Yes 
iteraid ITERAID_Service_Install c:\windows\system32\drivers\iteraid.sys Kernel Driver Yes Boot Running OK Normal No Yes 
kbdclass Keyboard Class Driver c:\windows\system32\drivers\kbdclass.sys Kernel Driver Yes System Running OK Normal No Yes 
kbdhid Keyboard HID Driver c:\windows\system32\drivers\kbdhid.sys Kernel Driver No System Stopped OK Ignore No No 
ksecdd KSecDD c:\windows\system32\drivers\ksecdd.sys Kernel Driver Yes Boot Running OK Critical No Yes 
lltdio Link-Layer Topology Discovery Mapper I/O Driver c:\windows\system32\drivers\lltdio.sys Kernel Driver Yes Auto Running OK Normal No Yes 
lsi_fc LSI_FC c:\windows\system32\drivers\lsi_fc.sys Kernel Driver Yes Boot Running OK Normal No Yes 
lsi_sas LSI_SAS c:\windows\system32\drivers\lsi_sas.sys Kernel Driver Yes Boot Running OK Normal No Yes 
lsi_scsi LSI_SCSI c:\windows\system32\drivers\lsi_scsi.sys Kernel Driver Yes Boot Running OK Normal No Yes 
luafv UAC File Virtualization c:\windows\system32\drivers\luafv.sys File System Driver Yes Auto Running OK Normal No Yes 
mdmxsdk mdmxsdk c:\windows\system32\drivers\mdmxsdk.sys Kernel Driver Yes Auto Running OK Ignore No Yes 
megasas megasas c:\windows\system32\drivers\megasas.sys Kernel Driver Yes Boot Running OK Normal No Yes 
megasr MegaSR c:\windows\system32\drivers\megasr.sys Kernel Driver Yes Boot Running OK Normal No Yes 
modem Modem c:\windows\system32\drivers\modem.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
monitor Microsoft Monitor Class Function Driver Service c:\windows\system32\drivers\monitor.sys Kernel Driver Yes Manual Running OK Normal No Yes 
mouclass Mouse Class Driver c:\windows\system32\drivers\mouclass.sys Kernel Driver Yes System Running OK Normal No Yes 
mouhid Mouse HID Driver c:\windows\system32\drivers\mouhid.sys Kernel Driver No Manual Stopped OK Ignore No No 
mountmgr Mount Point Manager c:\windows\system32\drivers\mountmgr.sys Kernel Driver Yes Boot Running OK Critical No Yes 
mpio Microsoft Multi-Path Bus Driver c:\windows\system32\drivers\mpio.sys Kernel Driver Yes Boot Running OK Normal No Yes 
mpsdrv Windows Firewall Authorization Driver c:\windows\system32\drivers\mpsdrv.sys Kernel Driver Yes Manual Running OK Normal No Yes 
mraid35x Mraid35x c:\windows\system32\drivers\mraid35x.sys Kernel Driver Yes Boot Running OK Normal No Yes 
mrxdav WebDav Client Redirector Driver c:\windows\system32\drivers\mrxdav.sys File System Driver Yes Manual Running OK Normal No Yes 
mrxsmb SMB MiniRedirector Wrapper and Engine c:\windows\system32\drivers\mrxsmb.sys File System Driver Yes Manual Running OK Normal No Yes 
mrxsmb10 SMB 1.x MiniRedirector c:\windows\system32\drivers\mrxsmb10.sys File System Driver Yes Manual Running OK Normal No Yes 
mrxsmb20 SMB 2.0 MiniRedirector c:\windows\system32\drivers\mrxsmb20.sys File System Driver Yes Manual Running OK Normal No Yes 
msahci msahci c:\windows\system32\drivers\msahci.sys Kernel Driver Yes Boot Running OK Critical No Yes 
msdsm Microsoft Multi-Path Device Specific Module c:\windows\system32\drivers\msdsm.sys Kernel Driver Yes Boot Running OK Normal No Yes 
msfs Msfs c:\windows\system32\drivers\msfs.sys File System Driver Yes System Running OK Normal No Yes 
msisadrv ISA/EISA Class Driver c:\windows\system32\drivers\msisadrv.sys Kernel Driver Yes Boot Running OK Critical No Yes 
mskssrv Microsoft Streaming Service Proxy c:\windows\system32\drivers\mskssrv.sys Kernel Driver No Manual Stopped OK Normal No No 
mspclock Microsoft Streaming Clock Proxy c:\windows\system32\drivers\mspclock.sys Kernel Driver No Manual Stopped OK Normal No No 
mspqm Microsoft Streaming Quality Manager Proxy c:\windows\system32\drivers\mspqm.sys Kernel Driver No Manual Stopped OK Normal No No 
msrpc MsRPC c:\windows\system32\drivers\msrpc.sys Kernel Driver No Manual Stopped OK Normal No No 
mssmbios Microsoft System Management BIOS Driver c:\windows\system32\drivers\mssmbios.sys Kernel Driver Yes Manual Running OK Normal No Yes 
mstee Microsoft Streaming Tee/Sink-to-Sink Converter c:\windows\system32\drivers\mstee.sys Kernel Driver No Manual Stopped OK Normal No No 
mup Mup c:\windows\system32\drivers\mup.sys File System Driver Yes Boot Running OK Normal No Yes 
nativewifip NativeWiFi Filter c:\windows\system32\drivers\nwifi.sys Kernel Driver Yes Manual Running OK Normal No Yes 
ndis NDIS System Driver c:\windows\system32\drivers\ndis.sys Kernel Driver Yes Boot Running OK Critical No Yes 
ndistapi Remote Access NDIS TAPI Driver c:\windows\system32\drivers\ndistapi.sys Kernel Driver Yes Manual Running OK Normal No Yes 
ndisuio NDIS Usermode I/O Protocol c:\windows\system32\drivers\ndisuio.sys Kernel Driver Yes Manual Running OK Normal No Yes 
ndiswan Remote Access NDIS WAN Driver c:\windows\system32\drivers\ndiswan.sys Kernel Driver Yes Manual Running OK Normal No Yes 
ndproxy NDIS Proxy c:\windows\system32\drivers\ndproxy.sys Kernel Driver Yes Manual Running OK Normal No Yes 
netbios NetBIOS Interface c:\windows\system32\drivers\netbios.sys File System Driver Yes System Running OK Normal No Yes 
netbt NETBT c:\windows\system32\drivers\netbt.sys Kernel Driver Yes System Running OK Normal No Yes 
netw3v32 Intel(R) PRO/Wireless 3945ABG Adapter Driver for Windows Vista 32 Bit c:\windows\system32\drivers\netw3v32.sys Kernel Driver No Manual Stopped OK Normal No No 
nfrd960 nfrd960 c:\windows\system32\drivers\nfrd960.sys Kernel Driver Yes Boot Running OK Normal No Yes 
npfs Npfs c:\windows\system32\drivers\npfs.sys File System Driver Yes System Running OK Normal No Yes 
nsiproxy NSI proxy service c:\windows\system32\drivers\nsiproxy.sys Kernel Driver Yes System Running OK Normal No Yes 
ntfs Ntfs c:\windows\system32\drivers\ntfs.sys File System Driver Yes Manual Running OK Normal No Yes 
ntrigdigi N-trig HID Tablet Driver c:\windows\system32\drivers\ntrigdigi.sys Kernel Driver No Manual Stopped OK Normal No No 
null Null c:\windows\system32\drivers\null.sys Kernel Driver Yes System Running OK Normal No Yes 
nvenetfd NVIDIA nForce Networking Controller Driver c:\windows\system32\drivers\nvmfdx32.sys Kernel Driver Yes Manual Running OK Normal No Yes 
nvhda Service for NVIDIA High Definition Audio Driver c:\windows\system32\drivers\nvhda32v.sys Kernel Driver Yes Manual Running OK Normal No Yes 
nvlddmkm nvlddmkm c:\windows\system32\drivers\nvlddmkm.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
nvraid NVIDIA nForce RAID Driver c:\windows\system32\drivers\nvraid.sys Kernel Driver Yes Boot Running OK Normal No Yes 
nvsmu nvsmu c:\windows\system32\drivers\nvsmu.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
nvstor nvstor c:\windows\system32\drivers\nvstor.sys Kernel Driver Yes Boot Running OK Critical No Yes 
nv_agp NVIDIA nForce AGP Bus Filter c:\windows\system32\drivers\nv_agp.sys Kernel Driver No Manual Stopped OK Normal No No 
ohci1394 RICOH OHCI Compliant IEEE 1394 Host Controller c:\windows\system32\drivers\ohci1394.sys Kernel Driver No Manual Stopped OK Normal No No 
parport Parallel port driver c:\windows\system32\drivers\parport.sys Kernel Driver No Manual Stopped OK Normal No No 
partmgr Partition Manager c:\windows\system32\drivers\partmgr.sys Kernel Driver Yes Boot Running OK Critical No Yes 
parvdm Parvdm c:\windows\system32\drivers\parvdm.sys Kernel Driver No Auto Stopped OK Ignore No No 
pci PCI Bus Driver c:\windows\system32\drivers\pci.sys Kernel Driver Yes Boot Running OK Critical No Yes 
pciide pciide c:\windows\system32\drivers\pciide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
pcmcia pcmcia c:\windows\system32\drivers\pcmcia.sys Kernel Driver No Manual Stopped OK Normal No No 
peauth PEAUTH c:\windows\system32\drivers\peauth.sys Kernel Driver Yes Auto Running OK Normal No Yes 
pptpminiport WAN Miniport (PPTP) c:\windows\system32\drivers\raspptp.sys Kernel Driver Yes Manual Running OK Normal No Yes 
processor Processor Driver c:\windows\system32\drivers\processr.sys Kernel Driver Yes Manual Running OK Normal No Yes 
psched QoS Packet Scheduler c:\windows\system32\drivers\pacer.sys Kernel Driver Yes System Running OK Normal No Yes 
ql2300 QLogic Fibre Channel Miniport Driver c:\windows\system32\drivers\ql2300.sys Kernel Driver Yes Boot Running OK Normal No Yes 
ql40xx QLogic iSCSI Miniport Driver c:\windows\system32\drivers\ql40xx.sys Kernel Driver Yes Boot Running OK Normal No Yes 
qwavedrv QWAVE driver c:\windows\system32\drivers\qwavedrv.sys Kernel Driver No Manual Stopped OK Normal No No 
rasacd Remote Access Auto Connection Driver c:\windows\system32\drivers\rasacd.sys Kernel Driver Yes System Running OK Normal No Yes 
rasl2tp WAN Miniport (L2TP) c:\windows\system32\drivers\rasl2tp.sys Kernel Driver Yes Manual Running OK Normal No Yes 
raspppoe Remote Access PPPOE Driver c:\windows\system32\drivers\raspppoe.sys Kernel Driver Yes Manual Running OK Normal No Yes 
rassstp WAN Miniport (SSTP) c:\windows\system32\drivers\rassstp.sys Kernel Driver Yes Manual Running OK Normal No Yes 
rdbss Redirected Buffering Sub Sysytem c:\windows\system32\drivers\rdbss.sys File System Driver Yes System Running OK Normal No Yes 
rdpcdd RDPCDD c:\windows\system32\drivers\rdpcdd.sys Kernel Driver Yes System Running OK Ignore No Yes 
rdpdr Terminal Server Device Redirector Driver c:\windows\system32\drivers\rdpdr.sys Kernel Driver No Manual Stopped OK Normal No No 
rdpencdd RDP Encoder Mirror Driver c:\windows\system32\drivers\rdpencdd.sys Kernel Driver Yes System Running OK Ignore No Yes 
rdpwd RDP Winstation Driver c:\windows\system32\drivers\rdpwd.sys Kernel Driver No Manual Stopped OK Ignore No No 
rspndr Link-Layer Topology Discovery Responder c:\windows\system32\drivers\rspndr.sys Kernel Driver Yes Auto Running OK Normal No Yes 
rtstor Realtek USB 2.0 Card Reader c:\windows\system32\drivers\rtstor.sys Kernel Driver Yes Manual Running OK Normal No Yes 
sbp2port SBP-2 Transport/Protocol Bus Driver c:\windows\system32\drivers\sbp2port.sys Kernel Driver Yes Boot Running OK Normal No Yes 
sdbus sdbus c:\windows\system32\drivers\sdbus.sys Kernel Driver No Manual Stopped OK Normal No No 
secdrv Security Driver c:\windows\system32\drivers\secdrv.sys Kernel Driver Yes Auto Running OK Normal No Yes 
serenum Serenum Filter Driver c:\windows\system32\drivers\serenum.sys Kernel Driver No Manual Stopped OK Normal No No 
serial Serial Port Driver c:\windows\system32\drivers\serial.sys Kernel Driver No Manual Stopped OK Ignore No No 
sermouse Serial Mouse Driver c:\windows\system32\drivers\sermouse.sys Kernel Driver No Manual Stopped OK Normal No No 
sffdisk SFF Storage Class Driver c:\windows\system32\drivers\sffdisk.sys Kernel Driver No Manual Stopped OK Normal No No 
sffp_mmc SFF Storage Protocol Driver for MMC c:\windows\system32\drivers\sffp_mmc.sys Kernel Driver No Manual Stopped OK Normal No No 
sffp_sd SFF Storage Protocol Driver for SDBus c:\windows\system32\drivers\sffp_sd.sys Kernel Driver No Manual Stopped OK Normal No No 
sfloppy High-Capacity Floppy Disk Drive c:\windows\system32\drivers\sfloppy.sys Kernel Driver No Manual Stopped OK Normal No No 
sisagp SIS AGP Bus Filter c:\windows\system32\drivers\sisagp.sys Kernel Driver No Manual Stopped OK Normal No No 
sisraid2 SiSRaid2 c:\windows\system32\drivers\sisraid2.sys Kernel Driver Yes Boot Running OK Normal No Yes 
sisraid4 SiSRaid4 c:\windows\system32\drivers\sisraid4.sys Kernel Driver Yes Boot Running OK Normal No Yes 
smb Message-oriented TCP/IP and TCP/IPv6 Protocol (SMB session) c:\windows\system32\drivers\smb.sys Kernel Driver Yes System Running OK Normal No Yes 
spldr Security Processor Loader Driver c:\windows\system32\drivers\spldr.sys Kernel Driver Yes Boot Running OK Critical No Yes 
srv srv c:\windows\system32\drivers\srv.sys File System Driver Yes Manual Running OK Normal No Yes 
srv2 srv2 c:\windows\system32\drivers\srv2.sys File System Driver Yes Manual Running OK Normal No Yes 
srvnet srvnet c:\windows\system32\drivers\srvnet.sys File System Driver Yes Manual Running OK Normal No Yes 
swenum Software Bus Driver c:\windows\system32\drivers\swenum.sys Kernel Driver Yes Manual Running OK Normal No Yes 
symc8xx Symc8xx c:\windows\system32\drivers\symc8xx.sys Kernel Driver Yes Boot Running OK Normal No Yes 
sym_hi Sym_hi c:\windows\system32\drivers\sym_hi.sys Kernel Driver Yes Boot Running OK Normal No Yes 
sym_u3 Sym_u3 c:\windows\system32\drivers\sym_u3.sys Kernel Driver Yes Boot Running OK Normal No Yes 
syntp Synaptics TouchPad Driver c:\windows\system32\drivers\syntp.sys Kernel Driver Yes Manual Running OK Normal No Yes 
tcpip TCP/IP Protocol Driver c:\windows\system32\drivers\tcpip.sys Kernel Driver Yes Boot Running OK Normal No Yes 
tcpip6 Microsoft IPv6 Protocol Driver c:\windows\system32\drivers\tcpip.sys Kernel Driver No Manual Stopped OK Normal No No 
tcpipreg TCP/IP Registry Compatibility c:\windows\system32\drivers\tcpipreg.sys Kernel Driver Yes Auto Running OK Normal No Yes 
tdpipe TDPIPE c:\windows\system32\drivers\tdpipe.sys Kernel Driver No Manual Stopped OK Normal No No 
tdtcp TDTCP c:\windows\system32\drivers\tdtcp.sys Kernel Driver No Manual Stopped OK Normal No No 
tdx NetIO Legacy TDI Support Driver c:\windows\system32\drivers\tdx.sys Kernel Driver Yes System Running OK Normal No Yes 
termdd Terminal Device Driver c:\windows\system32\drivers\termdd.sys Kernel Driver Yes System Running OK Normal No Yes 
tssecsrv Terminal Services Security Filter Driver c:\windows\system32\drivers\tssecsrv.sys Kernel Driver No Manual Stopped OK Ignore No No 
tunmp Microsoft Tun Miniport Adapter Driver c:\windows\system32\drivers\tunmp.sys Kernel Driver Yes Manual Running OK Normal No Yes 
tunnel Microsoft IPv6 Tunnel Miniport Adapter Driver c:\windows\system32\drivers\tunnel.sys Kernel Driver Yes Manual Running OK Normal No Yes 
uagp35 Microsoft AGPv3.5 Filter c:\windows\system32\drivers\uagp35.sys Kernel Driver No Manual Stopped OK Normal No No 
udfs udfs c:\windows\system32\drivers\udfs.sys File System Driver No Disabled Stopped OK Normal No No 
uliagpkx Uli AGP Bus Filter c:\windows\system32\drivers\uliagpkx.sys Kernel Driver No Manual Stopped OK Normal No No 
uliahci uliahci c:\windows\system32\drivers\uliahci.sys Kernel Driver Yes Boot Running OK Normal No Yes 
ulsata UlSata c:\windows\system32\drivers\ulsata.sys Kernel Driver Yes Boot Running OK Normal No Yes 
ulsata2 ulsata2 c:\windows\system32\drivers\ulsata2.sys Kernel Driver Yes Boot Running OK Normal No Yes 
umbus UMBus Enumerator Driver c:\windows\system32\drivers\umbus.sys Kernel Driver Yes Manual Running OK Normal No Yes 
usbccgp Microsoft USB Generic Parent Driver c:\windows\system32\drivers\usbccgp.sys Kernel Driver No Manual Stopped OK Normal No No 
usbcir eHome Infrared Receiver (USBCIR) c:\windows\system32\drivers\usbcir.sys Kernel Driver No Manual Stopped OK Normal No No 
usbehci Microsoft USB 2.0 Enhanced Host Controller Miniport Driver c:\windows\system32\drivers\usbehci.sys Kernel Driver Yes Manual Running OK Normal No Yes 
usbhub USB2 Enabled Hub c:\windows\system32\drivers\usbhub.sys Kernel Driver Yes Manual Running OK Normal No Yes 
usbohci Microsoft USB Open Host Controller Miniport Driver c:\windows\system32\drivers\usbohci.sys Kernel Driver Yes Manual Running OK Normal No Yes 
usbprint Microsoft USB PRINTER Class c:\windows\system32\drivers\usbprint.sys Kernel Driver No Manual Stopped OK Normal No No 
usbstor USB Mass Storage Driver c:\windows\system32\drivers\usbstor.sys Kernel Driver No Manual Stopped OK Normal No No 
usbuhci Microsoft USB Universal Host Controller Miniport Driver c:\windows\system32\drivers\usbuhci.sys Kernel Driver No Manual Stopped OK Normal No No 
vga vga c:\windows\system32\drivers\vgapnp.sys Kernel Driver No Manual Stopped OK Ignore No No 
vgasave VgaSave c:\windows\system32\drivers\vga.sys Kernel Driver Yes System Running OK Ignore No Yes 
viaagp VIA AGP Bus Filter c:\windows\system32\drivers\viaagp.sys Kernel Driver No Manual Stopped OK Normal No No 
viac7 VIA C7 Processor Driver c:\windows\system32\drivers\viac7.sys Kernel Driver No Manual Stopped OK Normal No No 
viaide viaide c:\windows\system32\drivers\viaide.sys Kernel Driver Yes Boot Running OK Critical No Yes 
volmgr Volume Manager Driver c:\windows\system32\drivers\volmgr.sys Kernel Driver Yes Boot Running OK Critical No Yes 
volmgrx Dynamic Volume Manager c:\windows\system32\drivers\volmgrx.sys Kernel Driver Yes Boot Running OK Critical No Yes 
volsnap Storage volumes c:\windows\system32\drivers\volsnap.sys Kernel Driver Yes Boot Running OK Critical No Yes 
vsmraid vsmraid c:\windows\system32\drivers\vsmraid.sys Kernel Driver Yes Boot Running OK Normal No Yes 
wacompen Wacom Serial Pen HID Driver c:\windows\system32\drivers\wacompen.sys Kernel Driver No Manual Stopped OK Normal No No 
wanarp Remote Access IP ARP Driver c:\windows\system32\drivers\wanarp.sys Kernel Driver No Manual Stopped OK Normal No No 
wanarpv6 Remote Access IPv6 ARP Driver c:\windows\system32\drivers\wanarp.sys Kernel Driver Yes System Running OK Normal No Yes 
wd Microsoft Watchdog Timer Driver c:\windows\system32\drivers\wd.sys Kernel Driver Yes Boot Running OK Normal No Yes 
wdf01000 Kernel Mode Driver Frameworks service c:\windows\system32\drivers\wdf01000.sys Kernel Driver Yes Boot Running OK Normal No Yes 
winachsf winachsf c:\windows\system32\drivers\hsx_cnxt.sys Kernel Driver Yes Manual Running OK Ignore No Yes 
wmiacpi Microsoft Windows Management Interface for ACPI c:\windows\system32\drivers\wmiacpi.sys Kernel Driver Yes Manual Running OK Normal No Yes 
ws2ifsl Winsock IFS driver c:\windows\system32\drivers\ws2ifsl.sys Kernel Driver No Disabled Stopped OK Normal No No 
wudfrd WUDFRd c:\windows\system32\drivers\wudfrd.sys Kernel Driver No Manual Stopped OK Normal No No 
xaudio XAudio c:\windows\system32\drivers\xaudio.sys Kernel Driver Yes Auto Running OK Ignore No Yes 
yukonwlh NDIS6.0 Miniport Driver for Marvell Yukon Ethernet Controller c:\windows\system32\drivers\yk60x86.sys Kernel Driver No Manual Stopped OK Normal No No 
[Signed Drivers]
Device Name Signed Device Class Driver Version Driver Date Manufacturer INF Name Driver Name Device ID 
Generic volume Yes VOLUME 6.0.6002.18005 6/21/2006 Microsoft volume.inf Not Available STORAGE\VOLUME\1&19F7E59C&0&SIGNATURE2D900954OFFSET37805DEA00LENGTH2B82D1800 
Generic volume Yes VOLUME 6.0.6002.18005 6/21/2006 Microsoft volume.inf Not Available STORAGE\VOLUME\1&19F7E59C&0&SIGNATURE2D900954OFFSET367E7D4C00LENGTH101E09E00 
Generic volume Yes VOLUME 6.0.6002.18005 6/21/2006 Microsoft volume.inf Not Available STORAGE\VOLUME\1&19F7E59C&0&SIGNATURE2D900954OFFSET1F025EFE00LENGTH177C1DD000 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT23 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT22 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT21 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT20 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT19 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT18 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT17 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT16 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT15 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT14 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT13 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT12 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT11 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT10 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT9 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT8 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT7 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT6 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT5 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT4 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT3 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT2 
Generic volume shadow copy Yes VOLUMESNAPSHOT 6.0.6000.16386 6/21/2006 Microsoft volsnap.inf Not Available STORAGE\VOLUMESNAPSHOT\HARDDISKVOLUMESNAPSHOT1 
Generic volume Yes VOLUME 6.0.6002.18005 6/21/2006 Microsoft volume.inf Not Available STORAGE\VOLUME\1&19F7E59C&0&SIGNATURE2D900954OFFSET7E00LENGTH1F025E0200 
Volume Manager Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ROOT\VOLMGR\0000 
UMBus Enumerator Yes SYSTEM 6.0.6001.18000 6/21/2006 Microsoft umbus.inf Not Available UMB\UMB\1&841921D&0&PRINTERBUSENUMERATOR 
UMBus Root Bus Enumerator Yes SYSTEM 6.0.6001.18000 6/21/2006 Microsoft umbus.inf Not Available ROOT\UMBUS\0000 
Microsoft System Management BIOS Driver Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ROOT\SYSTEM\0002 
Plug and Play Software Device Enumerator Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ROOT\SYSTEM\0000 
Terminal Server Mouse Driver Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ROOT\RDP_MOU\0000 
Terminal Server Keyboard Driver Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ROOT\RDP_KBD\0000 
WAN Miniport (SSTP) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netsstpa.inf Not Available ROOT\MS_SSTPMINIPORT\0000 
WAN Miniport (PPTP) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_PPTPMINIPORT\0000 
WAN Miniport (PPPOE) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_PPPOEMINIPORT\0000 
WAN Miniport (IPv6) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_NDISWANIPV6\0000 
WAN Miniport (IP) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_NDISWANIP\0000 
WAN Miniport (Network Monitor) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_NDISWANBH\0000 
WAN Miniport (L2TP) Yes NET 6.0.6001.18000 6/21/2006 Microsoft netrasa.inf Not Available ROOT\MS_L2TPMINIPORT\0000 
XAudio Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_XAUDIO\0000 
Kernel Mode Driver Frameworks service Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_WDF01000\0000 
Microsoft Watchdog Timer Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_WD\0000 
Remote Access IPv6 ARP Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_WANARPV6\0000 
vsmraid Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_VSMRAID\0000 
Storage volumes Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_VOLSNAP\0000 
Dynamic Volume Manager Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_VOLMGRX\0000 
viaide Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_VIAIDE\0000 
VgaSave Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_VGASAVE\0000 
ulsata2 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ULSATA2\0000 
UlSata Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ULSATA\0000 
uliahci Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ULIAHCI\0000 
NetIO Legacy TDI Support Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_TDX\0000 
TCP/IP Registry Compatibility Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_TCPIPREG\0000 
TCP/IP Protocol Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_TCPIP\0000 
Sym_u3 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SYM_U3\0000 
Sym_hi Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SYM_HI\0000 
Symc8xx Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SYMC8XX\0000 
Security Processor Loader Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SPLDR\0000 
Message-oriented TCP/IP and TCP/IPv6 Protocol (SMB session) Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SMB\0000 
SiSRaid4 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SISRAID4\0000 
SiSRaid2 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SISRAID2\0000 
Security Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SECDRV\0000 
SBP-2 Transport/Protocol Bus Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_SBP2PORT\0000 
Link-Layer Topology Discovery Responder Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_RSPNDR\0000 
RDP Encoder Mirror Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_RDPENCDD\0000 
RDPCDD Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_RDPCDD\0000 
Remote Access Auto Connection Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_RASACD\0000 
QLogic iSCSI Miniport Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_QL40XX\0000 
QLogic Fibre Channel Miniport Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_QL2300\0000 
QoS Packet Scheduler Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_PSCHED\0000 
PEAUTH Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_PEAUTH\0000 
nvstor Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NVSTOR\0000 
NVIDIA nForce RAID Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NVRAID\0000 
Null Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NULL\0000 
NSI proxy service Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NSIPROXY\0000 
nfrd960 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NFRD960\0000 
NETBT Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NETBT\0000 
NDProxy Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NDPROXY\0000 
NDIS Usermode I/O Protocol Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NDISUIO\0000 
NDIS System Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NDIS\0000 
NAVEX15 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NAVEX15\0000 
NAVENG Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NAVENG\0000 
NativeWiFi Filter Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_NATIVEWIFIP\0000 
ISA/EISA Class Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MSISADRV\0000 
Microsoft Multi-Path Device Specific Module Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MSDSM\0000 
msahci Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MSAHCI\0000 
Mraid35x Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MRAID35X\0000 
Windows Firewall Authorization Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MPSDRV\0000 
Mount Point Manager Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MOUNTMGR\0000 
MegaSR Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MEGASR\0000 
megasas Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_MEGASAS\0000 
LSI_SCSI Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_LSI_SCSI\0000 
LSI_SAS Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_LSI_SAS\0000 
LSI_FC Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_LSI_FC\0000 
Link-Layer Topology Discovery Mapper I/O Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_LLTDIO\0000 
KSecDD Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_KSECDD\0000 
ITERAID_Service_Install Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ITERAID\0000 
ITEATAPI_Service_Install Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ITEATAPI\0000 
PnP ISA/EISA Bus Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ISAPNP\0000 
intelide Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_INTELIDE\0000 
iirsp Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_IIRSP\0000 
Intel RAID Controller Vista Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_IASTORV\0000 
i2omp Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_I2OMP\0000 
HTTP Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_HTTP\0000 
HpCISSs Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_HPCISSS\0000 
elxstor Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ELXSTOR\0000 
LDDM Graphics Subsystem Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_DXGKRNL\0000 
Crcdisk Filter Driver Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_CRCDISK\0000 
cmdide Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_CMDIDE\0000 
Common Log (CLFS) Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_CLFS\0000 
Beep Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_BEEP\0000 
arcsas Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ARCSAS\0000 
arc Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ARC\0000 
amdide Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_AMDIDE\0000 
aliide Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ALIIDE\0000 
aic78xx Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_AIC78XX\0000 
Ancilliary Function Driver for Winsock Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_AFD\0000 
adpu320 Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ADPU320\0000 
adpu160m Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ADPU160M\0000 
adpahci Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ADPAHCI\0000 
adp94xx Not Available LEGACYDRIVER Not Available Not Available Not Available Not Available Not Available ROOT\LEGACY_ADP94XX\0000 
Microsoft iSCSI Initiator Yes SCSIADAPTER 6.0.6002.18005 6/21/2006 Microsoft iscsi.inf Not Available ROOT\ISCSIPRT\0000 
Microsoft Composite Battery Yes SYSTEM 6.0.6002.18005 6/21/2006 Microsoft acpi.inf Not Available ROOT\COMPOSITE_BATTERY\0000 
ACPI Fixed Feature Button Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\FIXEDBUTTON\2&DABA3FF&3 
System board Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C01\2&DABA3FF&3 
ACPI Power Button Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C0C\2&DABA3FF&3 
High precision event timer Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0103\0 
PCI standard host CPU bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_1022&DEV_1304&SUBSYS_00000000&REV_00\3&2411E6FE&0&C4 
PCI standard host CPU bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_1022&DEV_1303&SUBSYS_00000000&REV_00\3&2411E6FE&0&C3 
PCI standard host CPU bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_1022&DEV_1302&SUBSYS_00000000&REV_00\3&2411E6FE&0&C2 
PCI standard host CPU bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_1022&DEV_1301&SUBSYS_00000000&REV_00\3&2411E6FE&0&C1 
PCI standard host CPU bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_1022&DEV_1300&SUBSYS_00000000&REV_40\3&2411E6FE&0&C0 
Atheros AR5007 802.11b/g WiFi Adapter Yes NET 7.6.0.114 4/27/2008 Atheros Communications Inc. oem3.inf Not Available PCI\VEN_168C&DEV_001C&SUBSYS_137A103C&REV_01\4&B224E5E&0&00A0 
PCI standard PCI-to-PCI bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_077A&SUBSYS_000010DE&REV_A1\3&2411E6FE&0&A0 
Generic PnP Monitor Yes MONITOR 6.0.6001.18000 6/21/2006 (Standard monitor types) monitor.inf Not Available DISPLAY\SEC3451\5&156CF085&0&UID280 
NVIDIA GeForce 8200M G Yes DISPLAY 7.15.11.7614 7/11/2008 NVIDIA oem8.inf Not Available PCI\VEN_10DE&DEV_0845&SUBSYS_360A103C&REV_A2\4&105D929E&0&0058 
PCI standard PCI-to-PCI bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_0569&SUBSYS_000010DE&REV_A1\3&2411E6FE&0&58 
NVIDIA nForce Networking Controller Yes NET 67.7.6.1 2/19/2008 NVIDIA oem6.inf Not Available PCI\VEN_10DE&DEV_0760&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&50 
Disk drive Yes DISKDRIVE 6.0.6002.18005 6/21/2006 (Standard disk drives) disk.inf Not Available IDE\DISKSAMSUNG_HM251JI_________________________2SS00_03\5&8EB2AE7&0&1.0.0 
IDE Channel Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCIIDE\IDECHANNEL\4&26AC2C3E&0&1 
CD-ROM Drive Yes CDROM 6.0.6002.18005 6/21/2006 (Standard CD-ROM drives) cdrom.inf Not Available IDE\CDROMOPTIARC_DVD_RW_AD-7580S_________________FH03____\5&1BA4DB8C&0&0.0.0 
IDE Channel Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCIIDE\IDECHANNEL\4&26AC2C3E&0&0 
Standard Dual Channel PCI IDE Controller Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCI\VEN_10DE&DEV_0AD0&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&48 
PCI standard PCI-to-PCI bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_075A&SUBSYS_CB8410DE&REV_A1\3&2411E6FE&0&40 
NVIDIA HDMI Audio Yes MEDIA 1.0.0.27 5/9/2008 NVIDIA oem7.inf nvhda32v.sys HDAUDIO\FUNC_01&VEN_10DE&DEV_0002&SUBSYS_10DE0101&REV_1000\4&7CC389&0&0301 
HDAUDIO Soft Data Fax Modem with SmartCP Yes MODEM 7.70.0.0 11/15/2007 CXT oem10.inf Not Available HDAUDIO\FUNC_02&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0002 
Conexant High Definition SmartAudio 221 Yes MEDIA 4.58.0.0 6/10/2008 Conexant oem11.inf CHDRT32.sys HDAUDIO\FUNC_01&VEN_14F1&DEV_5051&SUBSYS_103C360A&REV_1000\4&7CC389&0&0001 
High Definition Audio Controller Yes SYSTEM 6.0.6002.18005 6/21/2006 Microsoft hdaudbus.inf Not Available PCI\VEN_10DE&DEV_0774&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&38 
IDE Channel Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCIIDE\IDECHANNEL\4&12D80BB5&0&1 
IDE Channel Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCIIDE\IDECHANNEL\4&12D80BB5&0&0 
Standard Dual Channel PCI IDE Controller Yes HDC 6.0.6002.18005 6/21/2006 (Standard IDE ATA/ATAPI controllers) mshdc.inf Not Available PCI\VEN_10DE&DEV_0759&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&30 
USB Root Hub Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available USB\ROOT_HUB20\4&2892721E&0 
Standard Enhanced PCI to USB Host Controller Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available PCI\VEN_10DE&DEV_077E&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&21 
USB Root Hub Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available USB\ROOT_HUB\4&266F08A&0 
Standard OpenHCD USB Host Controller Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available PCI\VEN_10DE&DEV_077D&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&20 
Realtek USB 2.0 Card Reader Yes USB 6.0.6000.20109 9/19/2008 Realtek Semiconductor Corp. oem12.inf Not Available USB\VID_0BDA&PID_0158\20071114173400000 
USB Root Hub Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available USB\ROOT_HUB20\4&3B437083&0 
Standard Enhanced PCI to USB Host Controller Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available PCI\VEN_10DE&DEV_077C&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&11 
USB Root Hub Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available USB\ROOT_HUB\4&3817B2FC&0 
Standard OpenHCD USB Host Controller Yes USB 6.0.6002.18005 6/21/2006 (Standard USB Host Controller) usbport.inf Not Available PCI\VEN_10DE&DEV_077B&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&10 
PCI standard RAM Controller Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_0568&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&0C 
NVIDIA nForce System Management Controller Yes SYSTEM 5.1.2600.150 4/24/2008 NVIDIA oem5.inf Not Available PCI\VEN_10DE&DEV_0753&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&0B 
NVIDIA nForce PCI System Management Yes SYSTEM 4.6.4.0 1/17/2008 NVIDIA oem4.inf Not Available PCI\VEN_10DE&DEV_0752&SUBSYS_360A103C&REV_A1\3&2411E6FE&0&09 
Motherboard resources Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C02\3 
Microsoft AC Adapter Yes BATTERY 6.0.6001.18000 6/21/2006 Microsoft battery.inf Not Available ACPI\ACPI0003\5&17D21A1&0 
Microsoft ACPI-Compliant Control Method Battery Yes BATTERY 6.0.6001.18000 6/21/2006 Microsoft battery.inf Not Available ACPI\PNP0C0A\1 
Microsoft ACPI-Compliant Embedded Controller Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C09\4&86EF4A8&0 
Synaptics PS/2 Port TouchPad Yes MOUSE 11.1.3.0 4/17/2008 Synaptics oem9.inf Not Available ACPI\SYN0158\4&86EF4A8&0 
Keyboard Filter Not Available Not Available Not Available Not Available Not Available Not Available Not Available {A87C2E0F-9A46-46B8-8EC4-E33355FBE1F7}\KEYBOARDFILTER\5&109848B6&0&01 
Standard 101/102-Key or Microsoft Natural PS/2 Keyboard with HP QLB Yes KEYBOARD 1.0.0.2 7/31/2008 Hewlett-Packard Development Company, L.P. oem2.inf Not Available ACPI\PNP0303\4&86EF4A8&0 
Numeric data processor Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C04\4&86EF4A8&0 
System CMOS/real time clock Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0B00\4&86EF4A8&0 
System speaker Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0800\4&86EF4A8&0 
Direct memory access controller Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0200\4&86EF4A8&0 
System timer Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0100\4&86EF4A8&0 
Programmable interrupt controller Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0000\4&86EF4A8&0 
Motherboard resources Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C02\1 
Motherboard resources Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C02\1F 
PCI standard ISA bridge Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_075E&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&08 
PCI standard RAM Controller Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available PCI\VEN_10DE&DEV_0754&SUBSYS_360A103C&REV_A2\3&2411E6FE&0&00 
PCI bus Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0A08\1 
ACPI Sleep Button Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C0E\2&DABA3FF&3 
ACPI Lid Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\PNP0C0D\2&DABA3FF&3 
Microsoft Windows Management Interface for ACPI Yes SYSTEM 6.0.6002.18005 6/21/2006 Microsoft acpi.inf Not Available ACPI\PNP0C14\0 
Processor Yes PROCESSOR 6.0.6001.18000 6/21/2006 (Standard processor types) cpu.inf Not Available ACPI\AUTHENTICAMD_-_X86_FAMILY_17_MODEL_3\_1 
Processor Yes PROCESSOR 6.0.6001.18000 6/21/2006 (Standard processor types) cpu.inf Not Available ACPI\AUTHENTICAMD_-_X86_FAMILY_17_MODEL_3\_0 
ACPI Thermal Zone Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\THERMALZONE\TZS1 
ACPI Thermal Zone Yes SYSTEM 6.0.6002.18005 6/21/2006 (Standard system devices) machine.inf Not Available ACPI\THERMALZONE\TZS0 
Microsoft ACPI-Compliant System Yes SYSTEM 6.0.6002.18005 6/21/2006 Microsoft acpi.inf Not Available ACPI_HAL\PNP0C08\0 
ACPI x86-based PC Yes COMPUTER 6.0.6002.18005 6/21/2006 (Standard computers) hal.inf Not Available ROOT\ACPI_HAL\0000 
Microsoft Tun Miniport Adapter Yes NET 6.0.6002.18005 6/21/2006 Microsoft nettun.inf Not Available ROOT\*TUNMP\0000 
Microsoft ISATAP Adapter Yes NET 6.0.6002.18005 6/21/2006 Microsoft nettun.inf Not Available ROOT\*ISATAP\0002 
Not Available Not Available Not Available Not Available Not Available Not Available Not Available Not Available HTREE\ROOT\0 
Not Available Yes Not Available 2:6.0,2:5.2,2:5.1,2:5.0 Not Available Not Available Not Available Not Available Microsoft XPS Document Writer 
[Environment Variables]
Variable Value User Name 
ComSpec %SystemRoot%\system32\cmd.exe <SYSTEM> 
FP_NO_HOST_CHECK NO <SYSTEM> 
OS Windows_NT <SYSTEM> 
Path %SystemRoot%\system32;%SystemRoot%;%SystemRoot%\System32\Wbem;C:\Program Files\CyberLink\Power2Go <SYSTEM> 
PATHEXT .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC <SYSTEM> 
PROCESSOR_ARCHITECTURE x86 <SYSTEM> 
TEMP %SystemRoot%\TEMP <SYSTEM> 
TMP %SystemRoot%\TEMP <SYSTEM> 
USERNAME SYSTEM <SYSTEM> 
windir %SystemRoot% <SYSTEM> 
PROCESSOR_LEVEL 17 <SYSTEM> 
PROCESSOR_IDENTIFIER x86 Family 17 Model 3 Stepping 1, AuthenticAMD <SYSTEM> 
PROCESSOR_REVISION 0301 <SYSTEM> 
NUMBER_OF_PROCESSORS 2 <SYSTEM> 
TRACE_FORMAT_SEARCH_PATH [\\NTREL202.ntdev.corp.microsoft.com\4F18C3A5-CA09-4DBD-B6FC-219FDD4C6BE0\TraceFormat]("file:///4F18C3A5-CA09-4DBD-B6FC-219FDD4C6BE0/TraceFormat") <SYSTEM> 
DFSTRACINGON FALSE <SYSTEM> 
OnlineServices Online Services <SYSTEM> 
Platform MCD <SYSTEM> 
PCBRAND Presario <SYSTEM> 
TEMP %USERPROFILE%\AppData\Local\Temp NT AUTHORITY\SYSTEM 
TMP %USERPROFILE%\AppData\Local\Temp NT AUTHORITY\SYSTEM 
TEMP %USERPROFILE%\AppData\Local\Temp user-PC\user 
TMP %USERPROFILE%\AppData\Local\Temp user-PC\user 
[Print Jobs]
Document Size Owner Notify Status Time Submitted Start Time Until Time Elapsed Time Pages Printed Job ID Priority Parameters Driver Print Processor Host Print Queue Data Type Name 
[Network Connections]
Local Name Remote Name Type Status User Name 
[Running Tasks]
Name Path Process ID Priority Min Working Set Max Working Set Start Time Version Size File Date 
system idle process Not Available 0 0 Not Available Not Available Not Available Not Available Not Available Not Available 
system Not Available 4 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
smss.exe Not Available 400 11 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
csrss.exe Not Available 528 13 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
csrss.exe Not Available 576 13 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
wininit.exe Not Available 584 13 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
services.exe Not Available 620 9 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
lsass.exe Not Available 632 9 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
lsm.exe Not Available 640 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 800 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
nvvsvc.exe Not Available 844 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
winlogon.exe Not Available 868 13 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 912 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 952 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1040 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1068 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1088 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
audiodg.exe Not Available 1180 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1212 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
slsvc.exe Not Available 1228 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
rundll32.exe Not Available 1320 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1352 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1536 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
spoolsv.exe Not Available 1740 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
wlanext.exe Not Available 1752 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1780 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 516 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
blservice.exe Not Available 664 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 896 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
svchost.exe Not Available 1568 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
searchindexer.exe Not Available 1808 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
taskeng.exe Not Available 1888 6 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
xaudio.exe Not Available 1528 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
taskeng.exe c:\windows\system32\taskeng.exe 2340 8 200 1380 1/3/2010 5:15 PM 6.0.6002.18005 166.00 KB (169,984 bytes) 1/3/2010 3:56 PM 
dwm.exe c:\windows\system32\dwm.exe 2384 13 51200 2097088 1/3/2010 5:15 PM 6.0.6002.18005 80.00 KB (81,920 bytes) 1/3/2010 3:54 PM 
explorer.exe c:\windows\explorer.exe 2504 8 200 1380 1/3/2010 5:15 PM 6.0.6002.18005 2.79 MB (2,926,592 bytes) 1/3/2010 3:54 PM 
syntpenh.exe c:\program files\synaptics\syntp\syntpenh.exe 2676 10 200 1380 1/3/2010 5:15 PM 11.1.3.0 1.00 MB (1,049,896 bytes) 4/17/2008 2:05 PM 
msascui.exe c:\program files\windows defender\msascui.exe 2692 8 200 1380 1/3/2010 5:15 PM 1.1.1600.0 984.55 KB (1,008,184 bytes) 1/20/2008 9:23 PM 
qlbctrl.exe c:\program files\hewlett-packard\hp quick launch buttons\qlbctrl.exe 2704 8 200 1380 1/3/2010 5:15 PM 6.4.8.2 197.30 KB (202,032 bytes) 10/25/2008 7:06 PM 
jusched.exe c:\program files\java\jre1.6.0_07\bin\jusched.exe 2716 8 200 1380 1/3/2010 5:15 PM 6.0.70.6 141.39 KB (144,784 bytes) 10/25/2008 8:13 PM 
hpwamain.exe c:\program files\hewlett-packard\hp wireless assistant\hpwamain.exe 2736 8 200 1380 1/3/2010 5:15 PM 3.0.9.1 477.30 KB (488,752 bytes) 4/15/2008 5:51 PM 
rundll32.exe c:\windows\system32\rundll32.exe 2860 8 200 1380 1/3/2010 5:15 PM 6.0.6000.16386 43.50 KB (44,544 bytes) 11/2/2006 4:48 AM 
hpqwmiex.exe Not Available 2884 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
wmiprvse.exe Not Available 2908 8 Not Available Not Available 1/3/2010 5:15 PM Not Available Not Available Not Available 
wifimsg.exe c:\program files\hewlett-packard\hp wireless assistant\wifimsg.exe 3076 8 200 1380 1/3/2010 5:15 PM 3.0.4.1 309.30 KB (316,720 bytes) 9/26/2007 10:34 AM 
com4qlbex.exe Not Available 3256 8 Not Available Not Available 1/3/2010 5:16 PM Not Available Not Available Not Available 
hpqtoaster.exe c:\program files\hewlett-packard\shared\hpqtoaster.exe 3416 8 200 1380 1/3/2010 5:16 PM 1.10.1.6 669.30 KB (685,360 bytes) 10/25/2008 7:06 PM 
syntphelper.exe Not Available 2416 10 Not Available Not Available 1/3/2010 5:17 PM Not Available Not Available Not Available 
hphc_service.exe Not Available 3020 8 Not Available Not Available 1/3/2010 5:17 PM Not Available Not Available Not Available 
iexplore.exe c:\program files\internet explorer\iexplore.exe 2144 8 200 1380 1/3/2010 6:12 PM 8.0.6001.18865 623.27 KB (638,232 bytes) 1/3/2010 1:35 PM 
iexplore.exe c:\program files\internet explorer\iexplore.exe 3580 8 200 1380 1/3/2010 6:12 PM 8.0.6001.18865 623.27 KB (638,232 bytes) 1/3/2010 1:35 PM 
wmiprvse.exe Not Available 3560 8 Not Available Not Available 1/3/2010 6:25 PM Not Available Not Available Not Available 
msinfo32.exe c:\windows\system32\msinfo32.exe 2600 8 200 1380 1/3/2010 6:26 PM 6.0.6002.18005 398.50 KB (408,064 bytes) 1/3/2010 3:55 PM 
searchprotocolhost.exe Not Available 2672 4 Not Available Not Available 1/3/2010 6:27 PM Not Available Not Available Not Available 
searchfilterhost.exe Not Available 3800 4 Not Available Not Available 1/3/2010 6:27 PM Not Available Not Available Not Available 
[Loaded Modules]
Name Version Size File Date Manufacturer Path 
taskeng 6.0.6002.18005 166.00 KB (169,984 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\taskeng.exe 
ntdll 6.0.6002.18005 1.15 MB (1,202,168 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\ntdll.dll 
kernel32 6.0.6002.18005 870.50 KB (891,392 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\kernel32.dll 
advapi32 6.0.6002.18005 782.00 KB (800,768 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\advapi32.dll 
rpcrt4 6.0.6002.18024 766.50 KB (784,896 bytes) 1/3/2010 1:21 PM Microsoft Corporation c:\windows\system32\rpcrt4.dll 
user32 6.0.6002.18005 613.00 KB (627,712 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\user32.dll 
gdi32 6.0.6002.18005 290.50 KB (297,472 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\gdi32.dll 
msvcrt 7.0.6002.18005 664.00 KB (679,936 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\msvcrt.dll 
shell32 6.0.6002.18005 11.05 MB (11,584,000 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\shell32.dll 
shlwapi 6.0.6002.18005 345.00 KB (353,280 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\shlwapi.dll 
ole32 6.0.6002.18005 1.26 MB (1,316,864 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\ole32.dll 
oleaut32 6.0.6002.18005 550.50 KB (563,712 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\oleaut32.dll 
secur32 6.0.6002.18051 71.00 KB (72,704 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\secur32.dll 
xmllite 1.2.1009.0 179.00 KB (183,296 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\xmllite.dll 
mpr 6.0.6002.18005 67.00 KB (68,608 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\mpr.dll 
imm32 6.0.6002.18005 112.00 KB (114,688 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\imm32.dll 
msctf 6.0.6002.18005 788.50 KB (807,424 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\msctf.dll 
lpk 6.0.6002.18051 23.00 KB (23,552 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\lpk.dll 
usp10 1.626.6002.18005 490.50 KB (502,272 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\usp10.dll 
comctl32 6.10.6002.18005 1.61 MB (1,686,016 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\winsxs\x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.6002.18005_none_5cb72f96088b0de0\comctl32.dll 
rsaenh 6.0.6002.18005 235.48 KB (241,128 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\rsaenh.dll 
clbcatq 2001.12.6931.18000 511.50 KB (523,776 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\clbcatq.dll 
tschannel 6.0.6000.16386 16.50 KB (16,896 bytes) 11/2/2006 4:40 AM Microsoft Corporation c:\windows\system32\tschannel.dll 
uxtheme 6.0.6001.18000 234.50 KB (240,128 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\uxtheme.dll 
hotstartuseragent 6.0.6001.18000 21.00 KB (21,504 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\hotstartuseragent.dll 
slc 6.0.6002.18005 223.00 KB (228,352 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\slc.dll 
playsndsrv 6.0.6001.18000 17.50 KB (17,920 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\playsndsrv.dll 
winmm 6.0.6002.18005 185.50 KB (189,952 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\winmm.dll 
oleacc 4.2.5406.0 210.00 KB (215,040 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\oleacc.dll 
dimsjob 6.0.6001.18000 34.50 KB (35,328 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\dimsjob.dll 
userenv 6.0.6002.18005 106.00 KB (108,544 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\userenv.dll 
ncrypt 6.0.6002.18005 199.50 KB (204,288 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\ncrypt.dll 
crypt32 6.0.6002.18005 956.00 KB (978,944 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\crypt32.dll 
msasn1 6.0.6002.18106 59.50 KB (60,928 bytes) 1/3/2010 1:21 PM Microsoft Corporation c:\windows\system32\msasn1.dll 
gpapi 6.0.6002.18005 73.50 KB (75,264 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\gpapi.dll 
msctfmonitor 6.0.6002.18005 19.00 KB (19,456 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\msctfmonitor.dll 
msutb 6.0.6002.18005 159.50 KB (163,328 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\msutb.dll 
dwmapi 6.0.6001.18000 39.00 KB (39,936 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\dwmapi.dll 
wtsapi32 6.0.6001.18000 26.00 KB (26,624 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\wtsapi32.dll 
pautoenr 6.0.6000.16386 42.00 KB (43,008 bytes) 11/2/2006 4:45 AM Microsoft Corporation c:\windows\system32\pautoenr.dll 
netapi32 6.0.6002.18005 456.50 KB (467,456 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\netapi32.dll 
psapi 6.0.6000.16386 12.00 KB (12,288 bytes) 11/2/2006 5:00 AM Microsoft Corporation c:\windows\system32\psapi.dll 
wldap32 6.0.6002.18005 281.00 KB (287,744 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\wldap32.dll 
ws2_32 6.0.6001.18000 175.00 KB (179,200 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\ws2_32.dll 
nsi 6.0.6001.18000 8.00 KB (8,192 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\nsi.dll 
certcli 6.0.6002.18005 316.00 KB (323,584 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\certcli.dll 
atl 3.5.2284.2 70.00 KB (71,680 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\atl.dll 
wininet 8.0.6001.18865 895.00 KB (916,480 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\wininet.dll 
normaliz 6.0.6000.16386 2.50 KB (2,560 bytes) 11/2/2006 4:33 AM Microsoft Corporation c:\windows\system32\normaliz.dll 
urlmon 8.0.6001.18865 1.15 MB (1,208,832 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\urlmon.dll 
iertutil 8.0.6001.18865 1.89 MB (1,985,536 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\iertutil.dll 
certenroll 6.0.6002.18005 1.06 MB (1,112,064 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\certenroll.dll 
ntdsapi 6.0.6001.18000 86.50 KB (88,576 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\ntdsapi.dll 
dnsapi 6.0.6002.18005 164.50 KB (168,448 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\dnsapi.dll 
winscard 6.0.6002.18005 113.00 KB (115,712 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\winscard.dll 
winsta 6.0.6001.18000 137.50 KB (140,800 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\winsta.dll 
wdmaud 6.0.6002.18005 163.50 KB (167,424 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\wdmaud.drv 
ksuser 6.0.6000.16386 4.50 KB (4,608 bytes) 11/2/2006 5:03 AM Microsoft Corporation c:\windows\system32\ksuser.dll 
mmdevapi 6.0.6002.18005 147.00 KB (150,528 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\mmdevapi.dll 
avrt 6.0.6001.18000 12.50 KB (12,800 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\avrt.dll 
setupapi 6.0.6002.18005 1.52 MB (1,591,296 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\setupapi.dll 
wintrust 6.0.6001.18000 167.50 KB (171,520 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\wintrust.dll 
imagehlp 6.0.6001.18000 149.50 KB (153,088 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\imagehlp.dll 
audioses 6.0.6002.18005 113.00 KB (115,712 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\audioses.dll 
audioeng 6.0.6001.18000 388.00 KB (397,312 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\audioeng.dll 
msacm32 6.0.6002.18005 21.00 KB (21,504 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\msacm32.drv 
msacm32 6.0.6001.18000 70.00 KB (71,680 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\msacm32.dll 
midimap 6.0.6002.18005 17.00 KB (17,408 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\midimap.dll 
tmm 6.0.6001.18000 1.24 MB (1,298,432 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\tmm.dll 
powrprof 6.0.6002.18005 96.50 KB (98,816 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\powrprof.dll 
d3d9 6.0.6002.18005 1.71 MB (1,788,416 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\d3d9.dll 
version 6.0.6002.18005 20.00 KB (20,480 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\version.dll 
d3d8thk 6.0.6000.16386 11.00 KB (11,264 bytes) 11/2/2006 5:03 AM Microsoft Corporation c:\windows\system32\d3d8thk.dll 
nvapi 7.15.11.7614 444.00 KB (454,656 bytes) 7/11/2008 2:31 PM NVIDIA Corporation c:\windows\system32\nvapi.dll 
apphelp 6.0.6002.18005 167.00 KB (171,008 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\apphelp.dll 
ntmarta 6.0.6002.18005 118.50 KB (121,344 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\ntmarta.dll 
samlib 6.0.6002.18005 56.00 KB (57,344 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\samlib.dll 
qagent 6.0.6001.18000 168.50 KB (172,544 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\qagent.dll 
fwpuclnt 6.0.6002.18005 581.50 KB (595,456 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\fwpuclnt.dll 
qutil 6.0.6001.18000 77.50 KB (79,360 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\qutil.dll 
wevtapi 6.0.6002.18005 244.50 KB (250,368 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\wevtapi.dll 
dwm 6.0.6002.18005 80.00 KB (81,920 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\dwm.exe 
dwmredir 6.0.6001.18000 80.00 KB (81,920 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\dwmredir.dll 
milcore 6.0.6002.18005 1.92 MB (2,012,160 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\milcore.dll 
nvd3dum 7.15.11.7614 5.61 MB (5,885,952 bytes) 7/11/2008 2:31 PM NVIDIA Corporation c:\windows\system32\nvd3dum.dll 
udwm 6.0.6002.18005 198.50 KB (203,264 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\udwm.dll 
windowscodecs 6.0.6002.18005 696.00 KB (712,704 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\windowscodecs.dll 
explorer 6.0.6002.18005 2.79 MB (2,926,592 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\explorer.exe 
shdocvw 6.0.6002.18005 1.02 MB (1,068,032 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\shdocvw.dll 
gdiplus 5.2.6002.18005 1.67 MB (1,748,992 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\winsxs\x86_microsoft.windows.gdiplus_6595b64144ccf1df_1.0.6002.18005_none_9e50b396ca17ae07\gdiplus.dll 
propsys 7.0.6002.18005 737.00 KB (754,688 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\propsys.dll 
browseui 6.0.6002.18005 1.26 MB (1,324,032 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\browseui.dll 
duser 6.0.6001.18000 179.50 KB (183,808 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\duser.dll 
ehstorshell 5.2.3790.1830 111.50 KB (114,176 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\ehstorshell.dll 
iconcodecservice 6.0.6000.16386 9.50 KB (9,728 bytes) 11/2/2006 8:34 AM Microsoft Corporation c:\windows\system32\iconcodecservice.dll 
timedate 6.0.6002.18005 697.50 KB (714,240 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\timedate.cpl 
actxprxy 6.0.6001.18000 319.00 KB (326,656 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\actxprxy.dll 
winbrand 6.0.6000.16386 849.00 KB (869,376 bytes) 11/2/2006 4:34 AM Microsoft Corporation c:\windows\system32\winbrand.dll 
msshsq 7.0.6002.18005 226.00 KB (231,424 bytes) 1/3/2010 3:57 PM Microsoft Corporation c:\windows\system32\msshsq.dll 
naturallanguage6 6.0.6002.18005 786.50 KB (805,376 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\naturallanguage6.dll 
authui 6.0.6002.18005 1.89 MB (1,985,024 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\authui.dll 
msimg32 6.0.6000.16386 4.50 KB (4,608 bytes) 11/2/2006 4:38 AM Microsoft Corporation c:\windows\system32\msimg32.dll 
msiltcfg 4.0.6000.16386 15.50 KB (15,872 bytes) 11/2/2006 4:42 AM Microsoft Corporation c:\windows\system32\msiltcfg.dll 
msi 4.5.6002.18005 2.14 MB (2,241,536 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\msi.dll 
linkinfo 6.0.6000.16386 21.50 KB (22,016 bytes) 11/2/2006 8:34 AM Microsoft Corporation c:\windows\system32\linkinfo.dll 
ieframe 8.0.6001.18865 10.56 MB (11,069,952 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\ieframe.dll 
cscapi 6.0.6002.18005 31.00 KB (31,744 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\cscapi.dll 
explorerframe 6.0.6002.18005 20.50 KB (20,992 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\explorerframe.dll 
mlang 6.0.6001.18000 183.50 KB (187,904 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\mlang.dll 
stobject 6.0.6002.18005 573.00 KB (586,752 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\stobject.dll 
batmeter 6.0.6000.16386 720.50 KB (737,792 bytes) 11/2/2006 4:48 AM Microsoft Corporation c:\windows\system32\batmeter.dll 
es 2001.12.6932.18005 262.50 KB (268,800 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\es.dll 
sndvolsso 6.0.6000.16386 181.50 KB (185,856 bytes) 11/2/2006 5:03 AM Microsoft Corporation c:\windows\system32\sndvolsso.dll 
ehsso 6.0.6002.18005 117.00 KB (119,808 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\ehome\ehsso.dll 
hid 6.0.6000.16386 21.50 KB (22,016 bytes) 11/2/2006 4:55 AM Microsoft Corporation c:\windows\system32\hid.dll 
netshell 6.0.6002.18005 3.03 MB (3,174,400 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\netshell.dll 
iphlpapi 6.0.6002.18005 89.50 KB (91,648 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\iphlpapi.dll 
dhcpcsvc 6.0.6002.18005 199.50 KB (204,288 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\dhcpcsvc.dll 
winnsi 6.0.6001.18000 14.50 KB (14,848 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\winnsi.dll 
dhcpcsvc6 6.0.6002.18005 127.50 KB (130,560 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\dhcpcsvc6.dll 
nlaapi 6.0.6001.18000 47.00 KB (48,128 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\nlaapi.dll 
firewallapi 6.0.6001.18000 394.50 KB (403,968 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\firewallapi.dll 
pnidui 6.0.6002.18005 1.74 MB (1,823,744 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\pnidui.dll 
wlanutil 6.0.6000.16386 8.00 KB (8,192 bytes) 11/2/2006 4:55 AM Microsoft Corporation c:\windows\system32\wlanutil.dll 
npmproxy 6.0.6000.16386 16.00 KB (16,384 bytes) 11/2/2006 4:59 AM Microsoft Corporation c:\windows\system32\npmproxy.dll 
nlsdata0009 6.0.6001.18000 4.65 MB (4,875,776 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\nlsdata0009.dll 
nlslexicons0009 6.0.6002.18005 2.52 MB (2,644,480 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\nlslexicons0009.dll 
wlanapi 6.0.6002.18064 63.50 KB (65,024 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\wlanapi.dll 
onex 6.0.6002.18005 1.47 MB (1,541,120 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\onex.dll 
eappprxy 6.0.6001.18000 40.50 KB (41,472 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\eappprxy.dll 
eappcfg 6.0.6002.18005 132.50 KB (135,680 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\eappcfg.dll 
bcrypt 6.0.6002.18005 268.00 KB (274,432 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\bcrypt.dll 
alttab 6.0.6000.16386 42.00 KB (43,008 bytes) 11/2/2006 8:34 AM Microsoft Corporation c:\windows\system32\alttab.dll 
wpdshserviceobj 6.0.6001.18000 128.50 KB (131,584 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\wpdshserviceobj.dll 
winhttp 6.0.6002.18096 368.50 KB (377,344 bytes) 1/3/2010 4:47 PM Microsoft Corporation c:\windows\system32\winhttp.dll 
srchadmin 7.0.6002.18005 294.50 KB (301,568 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\system32\srchadmin.dll 
ntshrui 6.0.6001.18000 290.00 KB (296,960 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\ntshrui.dll 
mssprxy 7.0.6002.18005 32.50 KB (33,280 bytes) 1/3/2010 3:57 PM Microsoft Corporation c:\windows\system32\mssprxy.dll 
webcheck 8.0.6001.18702 231.00 KB (236,544 bytes) 1/3/2010 1:34 PM Microsoft Corporation c:\windows\system32\webcheck.dll 
portabledevicetypes 6.0.6002.18005 157.00 KB (160,768 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\portabledevicetypes.dll 
synccenter 6.0.6002.18005 2.10 MB (2,205,184 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\synccenter.dll 
portabledeviceapi 6.0.6002.18005 235.50 KB (241,152 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\portabledeviceapi.dll 
wscntfy 6.0.6002.18005 218.50 KB (223,744 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wscntfy.dll 
wscapi 6.0.6002.18005 32.50 KB (33,280 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wscapi.dll 
sxs 6.0.6001.18000 368.00 KB (376,832 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\sxs.dll 
bthprops 6.0.6002.18005 625.50 KB (640,512 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\bthprops.cpl 
msxml3 8.100.5002.0 1.19 MB (1,248,768 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\msxml3.dll 
networkexplorer 6.0.6002.18005 2.12 MB (2,226,688 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\networkexplorer.dll 
dtsh 6.0.6000.16386 28.00 KB (28,672 bytes) 11/2/2006 4:56 AM Microsoft Corporation c:\windows\system32\dtsh.dll 
ndfapi 6.0.6001.18000 132.00 KB (135,168 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\ndfapi.dll 
wdi 6.0.6001.18000 72.00 KB (73,728 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\wdi.dll 
functiondiscoveryfolder 6.0.6002.18005 2.04 MB (2,134,528 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\functiondiscoveryfolder.dll 
winspool 6.0.6002.18005 252.00 KB (258,048 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\winspool.drv 
winsatapi 6.0.6001.18000 374.50 KB (383,488 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\winsatapi.dll 
msxml6 6.20.5002.0 1.34 MB (1,401,856 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\msxml6.dll 
cabinet 6.0.6001.18000 70.00 KB (71,680 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\cabinet.dll 
cryptnet 6.0.6001.18000 95.50 KB (97,792 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\cryptnet.dll 
sensapi 6.0.6000.16386 8.50 KB (8,704 bytes) 11/2/2006 4:50 AM Microsoft Corporation c:\windows\system32\sensapi.dll 
wlanpref 6.0.6002.18005 1.59 MB (1,671,680 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wlanpref.dll 
nci 6.0.6001.18000 72.50 KB (74,240 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\nci.dll 
wlanui 6.0.6002.18005 198.00 KB (202,752 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wlanui.dll 
wlanhlp 6.0.6002.18005 66.50 KB (68,096 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\wlanhlp.dll 
netprofm 6.0.6001.18000 231.50 KB (237,056 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\netprofm.dll 
rasmm 6.0.6001.18000 952.50 KB (975,360 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\rasmm.dll 
rasapi32 6.0.6002.18005 280.00 KB (286,720 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\rasapi32.dll 
rasman 6.0.6001.18000 69.50 KB (71,168 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\rasman.dll 
tapi32 6.0.6000.16386 187.00 KB (191,488 bytes) 11/2/2006 5:16 AM Microsoft Corporation c:\windows\system32\tapi32.dll 
rtutils 6.0.6002.18005 35.50 KB (36,352 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\rtutils.dll 
wlanmm 6.0.6001.18000 892.00 KB (913,408 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\wlanmm.dll 
thumbcache 6.0.6001.18000 78.50 KB (80,384 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\thumbcache.dll 
tquery 7.0.6002.18005 1.50 MB (1,576,960 bytes) 1/3/2010 3:57 PM Microsoft Corporation c:\windows\system32\tquery.dll 
syncui 6.0.6001.18000 171.50 KB (175,616 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\syncui.dll 
synceng 6.0.6001.18000 74.00 KB (75,776 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\synceng.dll 
syntpenh 11.1.3.0 1.00 MB (1,049,896 bytes) 4/17/2008 2:05 PM Synaptics, Inc. c:\program files\synaptics\syntp\syntpenh.exe 
comdlg32 6.0.6002.18005 440.00 KB (450,560 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\comdlg32.dll 
comctl32 5.82.6001.18000 519.50 KB (531,968 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\winsxs\x86_microsoft.windows.common-controls_6595b64144ccf1df_5.82.6001.18000_none_886786f450a74a05\comctl32.dll 
syncom 11.1.3.0 160.00 KB (163,840 bytes) 4/17/2008 1:16 PM Synaptics, Inc. c:\windows\system32\syncom.dll 
syntpapi 11.1.3.0 148.00 KB (151,552 bytes) 4/17/2008 1:28 PM Synaptics, Inc. c:\windows\system32\syntpapi.dll 
msascui 1.1.1600.0 984.55 KB (1,008,184 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\program files\windows defender\msascui.exe 
mpclient 1.1.1600.0 305.55 KB (312,888 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\program files\windows defender\mpclient.dll 
msmpres 1.1.1505.0 638.60 KB (653,928 bytes) 11/2/2006 8:34 AM Microsoft Corporation c:\program files\windows defender\msmpres.dll 
mprtmon 1.1.1600.0 655.55 KB (671,288 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\program files\windows defender\mprtmon.dll 
msftedit 5.41.21.2509 551.00 KB (564,224 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\msftedit.dll 
credssp 6.0.6001.18000 15.50 KB (15,872 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\credssp.dll 
schannel 6.0.6002.18051 264.50 KB (270,848 bytes) 1/3/2010 4:40 PM Microsoft Corporation c:\windows\system32\schannel.dll 
qlbctrl 6.4.8.2 197.30 KB (202,032 bytes) 10/25/2008 7:06 PM Hewlett-Packard Development Company, L.P. c:\program files\hewlett-packard\hp quick launch buttons\qlbctrl.exe 
QLBSERVICE 6.3.5.2 293.30 KB (300,336 bytes) 10/25/2008 7:06 PM Hewlett-Packard Development Company, L.P. c:\program files\hewlett-packard\hp quick launch buttons\qlbservice.dll 
hpqexec 6.3.4.2 217.30 KB (222,512 bytes) 10/25/2008 7:06 PM Hewlett-Packard Company c:\program files\hewlett-packard\hp quick launch buttons\hpqexec.dll 
wpdshext 6.0.6001.18000 2.42 MB (2,537,472 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\wpdshext.dll 
jusched 6.0.70.6 141.39 KB (144,784 bytes) 10/25/2008 8:13 PM Sun Microsystems, Inc. c:\program files\java\jre1.6.0_07\bin\jusched.exe 
hpwamain 3.0.9.1 477.30 KB (488,752 bytes) 4/15/2008 5:51 PM Hewlett-Packard Development Company, L.P. c:\program files\hewlett-packard\hp wireless assistant\hpwamain.exe 
rundll32 6.0.6000.16386 43.50 KB (44,544 bytes) 11/2/2006 4:48 AM Microsoft Corporation c:\windows\system32\rundll32.exe 
shimeng 6.0.6000.16386 108.50 KB (111,104 bytes) 11/2/2006 4:29 AM Microsoft Corporation c:\windows\system32\shimeng.dll 
aclayers 6.0.6002.18005 530.00 KB (542,720 bytes) 1/3/2010 3:53 PM Microsoft Corporation c:\windows\apppatch\aclayers.dll 
nvmctray 7.15.11.7614 90.53 KB (92,704 bytes) 7/11/2008 2:31 PM NVIDIA Corporation c:\windows\system32\nvmctray.dll 
wifimsg 3.0.4.1 309.30 KB (316,720 bytes) 9/26/2007 10:34 AM Hewlett-Packard Development Company, L.P. c:\program files\hewlett-packard\hp wireless assistant\wifimsg.exe 
oledlg 6.0.6001.18000 99.50 KB (101,888 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\oledlg.dll 
HpqToaster 1.10.1.6 669.30 KB (685,360 bytes) 10/25/2008 7:06 PM Not Available c:\program files\hewlett-packard\shared\hpqtoaster.exe 
iexplore 8.0.6001.18865 623.27 KB (638,232 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\program files\internet explorer\iexplore.exe 
mswsock 6.0.6002.18005 218.00 KB (223,232 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\mswsock.dll 
wshtcpip 6.0.6001.18000 9.00 KB (9,216 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\wshtcpip.dll 
wship6 6.0.6001.18000 9.00 KB (9,216 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\wship6.dll 
napinsp 6.0.6001.18000 49.00 KB (50,176 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\napinsp.dll 
pnrpnsp 6.0.6001.18000 61.00 KB (62,464 bytes) 1/20/2008 9:25 PM Microsoft Corporation c:\windows\system32\pnrpnsp.dll 
winrnr 6.0.6002.18005 19.50 KB (19,968 bytes) 1/3/2010 3:54 PM Microsoft Corporation c:\windows\system32\winrnr.dll 
rasadhlp 6.0.6000.16386 10.00 KB (10,240 bytes) 11/2/2006 4:58 AM Microsoft Corporation c:\windows\system32\rasadhlp.dll 
ieui 8.0.6001.18865 160.50 KB (164,352 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\ieui.dll 
ieproxy 8.0.6001.18865 240.50 KB (246,272 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\program files\internet explorer\ieproxy.dll 
msfeeds 8.0.6001.18865 580.50 KB (594,432 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\msfeeds.dll 
tiptsf 6.0.6002.18005 371.50 KB (380,416 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\program files\common files\microsoft shared\ink\tiptsf.dll 
mshtml 8.0.6001.18865 5.67 MB (5,940,736 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\mshtml.dll 
msls31 3.10.349.0 152.50 KB (156,160 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\msls31.dll 
ieshims 8.0.6001.18865 193.00 KB (197,632 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\program files\internet explorer\ieshims.dll 
AcroIEHelperShim 9.0.0.332 73.37 KB (75,128 bytes) 6/12/2008 1:33 AM Adobe Systems Incorporated c:\program files\common files\adobe\acrobat\activex\acroiehelpershim.dll 
msvcr80 8.0.50727.4016 617.83 KB (632,656 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\winsxs\x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.4016_none_d0893820442e7fe4\msvcr80.dll 
msvcp80 8.0.50727.4016 541.83 KB (554,832 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\winsxs\x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.4016_none_d0893820442e7fe4\msvcp80.dll 
AcroIEHelper 9.0.0.332 60.37 KB (61,816 bytes) 6/12/2008 1:33 AM Adobe Systems Incorporated c:\program files\common files\adobe\acrobat\activex\acroiehelper.dll 
ssv 6.0.70.6 497.39 KB (509,328 bytes) 10/25/2008 8:13 PM Sun Microsystems, Inc. c:\program files\java\jre1.6.0_07\bin\ssv.dll 
msvcr71 7.10.3052.4 340.00 KB (348,160 bytes) 6/10/2008 7:44 AM Microsoft Corporation c:\program files\java\jre1.6.0_07\bin\msvcr71.dll 
msimtf 6.0.6002.18005 30.50 KB (31,232 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\msimtf.dll 
jscript 5.8.6001.18795 709.50 KB (726,528 bytes) 1/3/2010 3:40 PM Microsoft Corporation c:\windows\system32\jscript.dll 
iepeers 8.0.6001.18865 180.00 KB (184,320 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\iepeers.dll 
imgutil 8.0.6001.18702 34.00 KB (34,816 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\imgutil.dll 
pngfilt 8.0.6001.18702 45.50 KB (46,592 bytes) 1/3/2010 1:34 PM Microsoft Corporation c:\windows\system32\pngfilt.dll 
flash9f 9.0.124.0 2.85 MB (2,991,488 bytes) 3/24/2008 10:32 PM Adobe Systems, Inc. c:\windows\system32\macromed\flash\flash9f.ocx 
dxtrans 8.0.6001.18702 211.00 KB (216,064 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\dxtrans.dll 
ddrawex 6.0.6000.16386 29.50 KB (30,208 bytes) 11/2/2006 5:03 AM Microsoft Corporation c:\windows\system32\ddrawex.dll 
ddraw 6.0.6001.18000 510.50 KB (522,752 bytes) 1/20/2008 9:24 PM Microsoft Corporation c:\windows\system32\ddraw.dll 
dciman32 6.0.6002.18051 10.00 KB (10,240 bytes) 1/3/2010 1:26 PM Microsoft Corporation c:\windows\system32\dciman32.dll 
dxtmsft 8.0.6001.18702 340.00 KB (348,160 bytes) 1/3/2010 1:35 PM Microsoft Corporation c:\windows\system32\dxtmsft.dll 
dispex 5.7.0.18000 32.00 KB (32,768 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\dispex.dll 
msinfo32 6.0.6002.18005 398.50 KB (408,064 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\msinfo32.exe 
mfc42u 6.6.8063.0 1.11 MB (1,160,704 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\mfc42u.dll 
odbc32 6.0.6002.18005 400.00 KB (409,600 bytes) 1/3/2010 3:55 PM Microsoft Corporation c:\windows\system32\odbc32.dll 
odbcint 6.0.6000.16386 224.00 KB (229,376 bytes) 11/2/2006 4:11 AM Microsoft Corporation c:\windows\system32\odbcint.dll 
wbemprox 6.0.6002.18005 29.50 KB (30,208 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wbem\wbemprox.dll 
wbemcomn 6.0.6001.18000 349.50 KB (357,888 bytes) 1/20/2008 9:23 PM Microsoft Corporation c:\windows\system32\wbemcomn.dll 
wbemsvc 6.0.6002.18005 48.00 KB (49,152 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wbem\wbemsvc.dll 
fastprox 6.0.6002.18005 600.50 KB (614,912 bytes) 1/3/2010 3:56 PM Microsoft Corporation c:\windows\system32\wbem\fastprox.dll 
[Services]
Display Name Name State Start Mode Service Type Path Error Control Start Name Tag ID 
Application Experience AeLookupSvc Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Application Layer Gateway Service ALG Stopped Manual Own Process c:\windows\system32\alg.exe Normal NT AUTHORITY\LocalService 0 
Application Information Appinfo Running Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Windows Audio Endpoint Builder AudioEndpointBuilder Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Windows Audio Audiosrv Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Base Filtering Engine BFE Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenonetwork Normal NT AUTHORITY\LocalService 0 
Background Intelligent Transfer Service BITS Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Computer Browser Browser Stopped Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Certificate Propagation CertPropSvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Microsoft .NET Framework NGEN v2.0.50727_X86 clr_optimization_v2.0.50727_32 Stopped Manual Own Process c:\windows\microsoft.net\framework\v2.0.50727\mscorsvw.exe Ignore LocalSystem 0 
Com4QLBEx Com4QLBEx Running Manual Own Process "c:\program files\hewlett-packard\hp quick launch buttons\com4qlbex.exe" Normal LocalSystem 0 
COM+ System Application COMSysApp Stopped Manual Own Process c:\windows\system32\dllhost.exe /processid:{02d4b3f1-fd88-11d1-960d-00805fc79235} Normal LocalSystem 0 
Cryptographic Services CryptSvc Running Auto Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT Authority\NetworkService 0 
DCOM Server Process Launcher DcomLaunch Running Auto Share Process c:\windows\system32\svchost.exe -k dcomlaunch Normal LocalSystem 0 
DFS Replication DFSR Stopped Manual Own Process c:\windows\system32\dfsr.exe Normal LocalSystem 0 
DHCP Client Dhcp Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT Authority\LocalService 0 
DNS Client Dnscache Running Auto Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
Wired AutoConfig dot3svc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal localSystem 0 
Diagnostic Policy Service DPS Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenonetwork Normal NT AUTHORITY\LocalService 0 
Extensible Authentication Protocol EapHost Running Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Windows Media Center Receiver Service ehRecvr Stopped Manual Own Process c:\windows\ehome\ehrecvr.exe Ignore NT AUTHORITY\networkService 0 
Windows Media Center Scheduler Service ehSched Stopped Manual Own Process c:\windows\ehome\ehsched.exe Ignore NT AUTHORITY\networkService 0 
Windows Media Center Service Launcher ehstart Stopped Auto Share Process c:\windows\system32\svchost.exe -k localservicenonetwork Ignore NT AUTHORITY\LocalService 0 
ReadyBoost EMDMgmt Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Ignore LocalSystem 0 
Windows Event Log Eventlog Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
COM+ Event System EventSystem Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Function Discovery Provider Host fdPHost Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Function Discovery Resource Publication FDResPub Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Windows Presentation Foundation Font Cache 3.0.0.0 FontCache3.0.0.0 Stopped Manual Own Process c:\windows\microsoft.net\framework\v3.0\wpf\presentationfontcache.exe Normal NT Authority\LocalService 0 
Group Policy Client gpsvc Running Auto Own Process c:\windows\system32\svchost.exe -k gpsvcgroup Normal LocalSystem 0 
Human Interface Device Access hidserv Stopped Manual Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Health Key and Certificate Management hkmsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
HP Health Check Service HP Health Check Service Running Auto Own Process "c:\program files\hewlett-packard\hp health check\hphc_service.exe" Normal LocalSystem 0 
hpqwmiex hpqwmiex Running Manual Own Process "c:\program files\hewlett-packard\shared\hpqwmiex.exe" Normal LocalSystem 0 
InstallDriver Table Manager IDriverT Stopped Manual Own Process "c:\program files\common files\installshield\driver\1050\intel 32\idrivert.exe" Ignore LocalSystem 0 
Windows CardSpace idsvc Stopped Manual Share Process "c:\windows\microsoft.net\framework\v3.0\windows communication foundation\infocard.exe" Normal LocalSystem 0 
IKE and AuthIP IPsec Keying Modules IKEEXT Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
PnP-X IP Bus Enumerator IPBusEnum Stopped Manual Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
IP Helper iphlpsvc Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
CNG Key Isolation KeyIso Running Manual Share Process c:\windows\system32\lsass.exe Normal LocalSystem 0 
KtmRm for Distributed Transaction Coordinator KtmRm Running Auto Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
Server LanmanServer Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Workstation LanmanWorkstation Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Link-Layer Topology Discovery Mapper lltdsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
TCP/IP NetBIOS Helper lmhosts Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Windows Media Center Extender Service Mcx2Svc Stopped Disabled Share Process c:\windows\system32\svchost.exe -k localservice Normal NT Authority\LocalService 0 
Multimedia Class Scheduler MMCSS Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Windows Firewall MpsSvc Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenonetwork Normal NT Authority\LocalService 0 
Distributed Transaction Coordinator MSDTC Stopped Manual Own Process c:\windows\system32\msdtc.exe Normal NT AUTHORITY\NetworkService 0 
Microsoft iSCSI Initiator Service MSiSCSI Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Windows Installer msiserver Stopped Manual Own Process c:\windows\system32\msiexec /v Normal LocalSystem 0 
Network Access Protection Agent napagent Stopped Manual Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
Netlogon Netlogon Stopped Manual Share Process c:\windows\system32\lsass.exe Normal LocalSystem 0 
Network Connections Netman Running Manual Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Network List Service netprofm Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Net.Tcp Port Sharing Service NetTcpPortSharing Stopped Disabled Share Process "c:\windows\microsoft.net\framework\v3.0\windows communication foundation\smsvchost.exe" Normal NT AUTHORITY\LocalService 0 
Network Location Awareness NlaSvc Running Auto Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
Norton Internet Security Norton Internet Security Stopped Auto Own Process "c:\program files\norton internet security\engine\16.0.0.125\ccsvchst.exe" /s "norton internet security" /m "c:\program files\norton internet security\engine\16.0.0.125\dimaster.dll" /prefetch:1 Normal LocalSystem 0 
Network Store Interface Service nsi Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT Authority\LocalService 0 
NVIDIA Display Driver Service nvsvc Running Auto Own Process c:\windows\system32\nvvsvc.exe Normal LocalSystem 0 
Peer Networking Identity Manager p2pimsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Peer Networking Grouping p2psvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Program Compatibility Assistant Service PcaSvc Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Performance Logs & Alerts pla Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenonetwork Normal NT AUTHORITY\LocalService 0 
Plug and Play PlugPlay Running Auto Share Process c:\windows\system32\svchost.exe -k dcomlaunch Normal LocalSystem 0 
PNRP Machine Name Publication Service PNRPAutoReg Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Peer Name Resolution Protocol PNRPsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
IPsec Policy Agent PolicyAgent Running Auto Share Process c:\windows\system32\svchost.exe -k networkservicenetworkrestricted Normal NT Authority\NetworkService 0 
User Profile Service ProfSvc Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Protected Storage ProtectedStorage Stopped Manual Share Process c:\windows\system32\lsass.exe Normal LocalSystem 0 
Quality Windows Audio Video Experience QWAVE Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Remote Access Auto Connection Manager RasAuto Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Remote Access Connection Manager RasMan Running Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Recovery Service for Windows Recovery Service for Windows Running Auto Own Process c:\program files\sminst\blservice.exe Normal LocalSystem 0 
Routing and Remote Access RemoteAccess Stopped Disabled Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Remote Registry RemoteRegistry Stopped Manual Share Process c:\windows\system32\svchost.exe -k regsvc Normal NT AUTHORITY\LocalService 0 
Remote Procedure Call (RPC) Locator RpcLocator Stopped Manual Own Process c:\windows\system32\locator.exe Normal NT AUTHORITY\NetworkService 0 
Remote Procedure Call (RPC) RpcSs Running Auto Share Process c:\windows\system32\svchost.exe -k rpcss Normal NT AUTHORITY\NetworkService 0 
Security Accounts Manager SamSs Running Auto Share Process c:\windows\system32\lsass.exe Normal LocalSystem 0 
Smart Card SCardSvr Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Task Scheduler Schedule Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Smart Card Removal Policy SCPolicySvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Windows Backup SDRSVC Stopped Manual Own Process c:\windows\system32\svchost.exe -k sdrsvc Normal localSystem 0 
Secondary Logon seclogon Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
System Event Notification Service SENS Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Terminal Services Configuration SessionEnv Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Internet Connection Sharing (ICS) SharedAccess Stopped Disabled Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Shell Hardware Detection ShellHWDetection Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Ignore LocalSystem 0 
Software Licensing slsvc Running Auto Own Process c:\windows\system32\slsvc.exe Normal NT AUTHORITY\NetworkService 0 
SL UI Notification Service SLUINotify Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
SNMP Trap SNMPTRAP Stopped Manual Own Process c:\windows\system32\snmptrap.exe Normal NT AUTHORITY\LocalService 0 
Print Spooler Spooler Running Auto Own Process c:\windows\system32\spoolsv.exe Normal LocalSystem 0 
SSDP Discovery SSDPSRV Running Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Secure Socket Tunneling Protocol Service SstpSvc Running Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT Authority\LocalService 0 
Windows Image Acquisition (WIA) stisvc Running Auto Own Process c:\windows\system32\svchost.exe -k imgsvc Normal NT Authority\LocalService 0 
Microsoft Software Shadow Copy Provider swprv Stopped Manual Own Process c:\windows\system32\svchost.exe -k swprv Normal LocalSystem 0 
Superfetch SysMain Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Ignore LocalSystem 0 
Tablet PC Input Service TabletInputService Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Telephony TapiSrv Running Manual Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
TPM Base Services TBS Stopped Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Terminal Services TermService Running Auto Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT Authority\NetworkService 0 
Themes Themes Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Thread Ordering Server THREADORDER Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Distributed Link Tracking Client TrkWks Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Windows Modules Installer TrustedInstaller Stopped Manual Own Process c:\windows\servicing\trustedinstaller.exe Normal localSystem 0 
Interactive Services Detection UI0Detect Stopped Manual Own Process c:\windows\system32\ui0detect.exe Normal LocalSystem 0 
UPnP Device Host upnphost Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Desktop Window Manager Session Manager UxSms Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal localSystem 0 
Virtual Disk vds Stopped Manual Own Process c:\windows\system32\vds.exe Normal LocalSystem 0 
Volume Shadow Copy VSS Stopped Manual Own Process c:\windows\system32\vssvc.exe Normal LocalSystem 0 
Windows Time W32Time Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Windows Connect Now - Config Registrar wcncsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Windows Color System WcsPlugInService Stopped Manual Share Process c:\windows\system32\svchost.exe -k wcssvc Normal NT AUTHORITY\LocalService 0 
Diagnostic Service Host WdiServiceHost Stopped Manual Share Process c:\windows\system32\svchost.exe -k wdisvc Normal NT AUTHORITY\LocalService 0 
Diagnostic System Host WdiSystemHost Running Manual Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
WebClient WebClient Running Auto Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Windows Event Collector Wecsvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
Problem Reports and Solutions Control Panel Support wercplsupport Stopped Manual Share Process c:\windows\system32\svchost.exe -k netsvcs Normal localSystem 0 
Windows Error Reporting Service WerSvc Running Auto Share Process c:\windows\system32\svchost.exe -k wersvcgroup Ignore localSystem 0 
Windows Defender WinDefend Running Auto Share Process c:\windows\system32\svchost.exe -k secsvcs Normal LocalSystem 0 
WinHTTP Web Proxy Auto-Discovery Service WinHttpAutoProxySvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservice Normal NT AUTHORITY\LocalService 0 
Windows Management Instrumentation Winmgmt Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Ignore localSystem 0 
Windows Remote Management (WS-Management) WinRM Stopped Manual Share Process c:\windows\system32\svchost.exe -k networkservice Normal NT AUTHORITY\NetworkService 0 
WLAN AutoConfig Wlansvc Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
WMI Performance Adapter wmiApSrv Stopped Manual Own Process c:\windows\system32\wbem\wmiapsrv.exe Normal localSystem 0 
Windows Media Player Network Sharing Service WMPNetworkSvc Stopped Manual Own Process "c:\program files\windows media player\wmpnetwk.exe" Normal NT AUTHORITY\NetworkService 0 
Parental Controls WPCSvc Stopped Manual Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT Authority\LocalService 0 
Portable Device Enumerator Service WPDBusEnum Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
Security Center wscsvc Running Auto Share Process c:\windows\system32\svchost.exe -k localservicenetworkrestricted Normal NT AUTHORITY\LocalService 0 
Windows Search WSearch Running Auto Own Process c:\windows\system32\searchindexer.exe /embedding Normal LocalSystem 0 
Windows Update wuauserv Running Auto Share Process c:\windows\system32\svchost.exe -k netsvcs Normal LocalSystem 0 
Windows Driver Foundation - User-mode Driver Framework wudfsvc Running Auto Share Process c:\windows\system32\svchost.exe -k localsystemnetworkrestricted Normal LocalSystem 0 
XAudioService XAudioService Running Auto Own Process c:\windows\system32\drivers\xaudio.exe Normal LocalSystem 0 
[Program Groups]
Group Name Name User Name 
Start Menu Default:Start Menu Default 
Start Menu\Programs Default:Start Menu\Programs Default 
Start Menu\Programs\Accessories Default:Start Menu\Programs\Accessories Default 
Start Menu\Programs\Accessories\Accessibility Default:Start Menu\Programs\Accessories\Accessibility Default 
Start Menu\Programs\Accessories\System Tools Default:Start Menu\Programs\Accessories\System Tools Default 
Start Menu\Programs\CyberLink DVD Suite Default:Start Menu\Programs\CyberLink DVD Suite Default 
Start Menu\Programs\Maintenance Default:Start Menu\Programs\Maintenance Default 
Start Menu Public:Start Menu Public 
Start Menu\Programs Public:Start Menu\Programs Public 
Start Menu\Programs\Accessories Public:Start Menu\Programs\Accessories Public 
Start Menu\Programs\Accessories\Accessibility Public:Start Menu\Programs\Accessories\Accessibility Public 
Start Menu\Programs\Accessories\System Tools Public:Start Menu\Programs\Accessories\System Tools Public 
Start Menu\Programs\Accessories\Tablet PC Public:Start Menu\Programs\Accessories\Tablet PC Public 
Start Menu\Programs\Administrative Tools Public:Start Menu\Programs\Administrative Tools Public 
Start Menu\Programs\Extras and Upgrades Public:Start Menu\Programs\Extras and Upgrades Public 
Start Menu\Programs\Games Public:Start Menu\Programs\Games Public 
Start Menu\Programs\HP Public:Start Menu\Programs\HP Public 
Start Menu\Programs\Maintenance Public:Start Menu\Programs\Maintenance Public 
Start Menu\Programs\muvee Public:Start Menu\Programs\muvee Public 
Start Menu\Programs\NetWaiting Public:Start Menu\Programs\NetWaiting Public 
Start Menu\Programs\Online Services Public:Start Menu\Programs\Online Services Public 
Start Menu\Programs\Online Services\United States Public:Start Menu\Programs\Online Services\United States Public 
Start Menu\Programs\Quicken Financial Center Public:Start Menu\Programs\Quicken Financial Center Public 
Start Menu\Programs\Recovery Manager Public:Start Menu\Programs\Recovery Manager Public 
Start Menu\Programs\Startup Public:Start Menu\Programs\Startup Public 
Start Menu\Programs\Tablet PC Public:Start Menu\Programs\Tablet PC Public 
Start Menu user-PC\user:Start Menu user-PC\user 
Start Menu\Programs user-PC\user:Start Menu\Programs user-PC\user 
Start Menu\Programs\Accessories user-PC\user:Start Menu\Programs\Accessories user-PC\user 
Start Menu\Programs\Accessories\Accessibility user-PC\user:Start Menu\Programs\Accessories\Accessibility user-PC\user 
Start Menu\Programs\Accessories\System Tools user-PC\user:Start Menu\Programs\Accessories\System Tools user-PC\user 
Start Menu\Programs\Administrative Tools user-PC\user:Start Menu\Programs\Administrative Tools user-PC\user 
Start Menu\Programs\CyberLink DVD Suite user-PC\user:Start Menu\Programs\CyberLink DVD Suite user-PC\user 
Start Menu\Programs\Maintenance user-PC\user:Start Menu\Programs\Maintenance user-PC\user 
Start Menu\Programs\Startup user-PC\user:Start Menu\Programs\Startup user-PC\user 
[Startup Programs]
Program Command User Name Location 
SynTPEnh c:\program files\synaptics\syntp\syntpenh.exe Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
UpdatePSTShortCut "c:\program files\cyberlink\dvd suite\muitransfer\muistartmenu.exe" "c:\program files\cyberlink\dvd suite" updatewithcreateonce "software\cyberlink\powerstarter" Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
Windows Defender %programfiles%\windows defender\msascui.exe -hide Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
QlbCtrl.exe c:\program files\hewlett-packard\hp quick launch buttons\qlbctrl.exe /start Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
SunJavaUpdateSched "c:\program files\java\jre1.6.0_07\bin\jusched.exe" Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
hpWirelessAssistant c:\program files\hewlett-packard\hp wireless assistant\hpwamain.exe Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
NvCplDaemon rundll32.exe c:\windows\system32\nvcpl.dll,nvstartup Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
NvMediaCenter rundll32.exe c:\windows\system32\nvmctray.dll,nvtaskbarinit Public HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 
[OLE Registration]
Object Local Server 
WordPad Document "%programfiles%\windows nt\accessories\wordpad.exe" 
Adobe Acrobat Document "c:\program files\adobe\reader 9.0\reader\acrord32.exe" 
Drawing Not Available 
Package Not Available 
Microsoft PenInputPanel Control Not Available 
[Windows Error Reporting]
Time Type Details 
```
 
 
Please help if you can. I would like to use Ubuntu from now on, done with the Windows issues and malware.

---

### Post by anewguy on 2010-01-05
Boot up ubuntu and go to a terminal window, then do the following:

lspci <press enter>

Completely copy the line for the wireless adapter and post it back here.

If the wireless adapter doesn't show in that output, then do the following:

lsusb <press enter>

Completely copy the line for the wireless adapter and post it back here.

Dave :)

---

### Post by inoh on 2010-01-05
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by anewguy on 2010-01-07
See if there are any drivers listed under hardware drivers.  If so, be sure they are enabled.  If not, try connecting via hard wire to your router, then do an update, then see if a driver shows up in hardware drivers.  If not, I think you may need to use the madwifi drivers.  There is a lot of information both in this forum and on the net itself that should get you going with those.

If you have problems or questions, please post back.

Dave :)

---

### Post by inoh on 2010-01-09
I have only had luck with net5211.inf and natathw.ing.  They are faster but only half speed.  None of the madwifi drivers will install properly for me.  From what I've seen posted around, net5217.inf will work better.  But I just can't seem to find it.  Could you help me out?

---

### Post by anewguy on 2010-01-09
I haven't been able to locate that file.

Sorry

Dave :)

---

