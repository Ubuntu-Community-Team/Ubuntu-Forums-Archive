---
title: "No audio at all"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by segamaster222 on 2010-08-21
I got the HP pavillion G62-208 from best buy and I installed ubuntu on it right away here are the specs of the laptop

> Product Number XA505UA#ABC
Microprocessor 2.1GHz VISION Technology from AMD with AMD Athlon II Dual-Core Processor for Notebook PCs P320
Microprocessor Cache 1MB L2 Cache
Memory 3GB DDR3 System Memory (2 DIMM)
Memory Max 8GB
Video Graphics ATI Mobility Radeon HD 4250 Graphics
Video Memory Up to 1405MB
Hard Drive 320GB (7200RPM)
Multimedia Drive LightScribe SuperMulti 8X DVD±R/RW with Double Layer Support
Display 15.6" diagonal High-Definition HP BrightView LED Display (1366 x 768)
Fax/Modem High-speed 56k modem
Network Card Integrated 10/100 Ethernet LAN
Wireless Connectivity •802.11b/g/n WLAN
Sound •Altec Lansing speakers
Keyboard 101-key compatible keyboard with One touch launch keys
Pointing Device Touch Pad with integrated On/Off button and 2-way scroll pad support
External Ports •5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
•3 Universal Serial Bus (USB) 2.0
•1 HDMI
•1 VGA (15-pin)
•1 RJ-11 (modem)
•1 RJ -45 (LAN)
•1 Headphone-out
•1 Microphone-in
Other Devices •HP Webcam with integrated microphone
Dimensions 14.72"(W)x 9.70"(D)x 1.25"(min H)/1.44"(max H)
Weight 5.50 lbs
Security •Kensington MicroSaver lock slot
•Power-on password
•Accepts 3rd party security lock devices
Power •65W AC Adapter
•6-Cell 47WHr Lithium-Ion Battery 

And output of **lspci** was

> james@james-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)



Hope i can get this issue resolved, I got wireless working all by myself.

---

### Post by segamaster222 on 2010-08-21
UPDATE: Without doing ANY updates or anything when I restarted sound just started working for some reason, will come back to this topic if i encounter any other problems.

Currently dual booting windows 7 x64 and ubuntu in preparation for a computer networking course I start in September...

---

