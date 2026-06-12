---
title: "No Sound"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Glix on 2009-07-07
I did a clean install of Ubuntu 9.04, and I'm not getting sound through one of the laptop's two sound cards, which controls the built in speakers and mic, I only get it through the headphone jack.

Sound information:
[http://www.alsa-project.org/db/?f=dd2a905f5ce8f298031477ed0e084609aca974e0](http://www.alsa-project.org/db/?f=dd2a905f5ce8f298031477ed0e084609aca974e0)

As far as I can tell ALSA is only recognising ATI and not the Realtek.

Any help at all would be appreciated, as I'm brand new to this, and aside this sound problem things are running great.

Thanks in advance, let me know if you need any more information.

---

### Post by brianfactors on 2009-07-07
Please open the terminal (Applications > Accessories > Terminal) and type ```
lspci
```. The results would be helpful in determining what hardware your using.

Secondly, though. Just a thought: ubuntu actually has as many as three sound architectures going: PulseAudio, ALSA, and OSS. On my computer, I had a lot of problems with Pulse Audio. Why don't you try to uninstall it? You can find the package in synzptic (pulseaudio) or you can just type into the terminal:
```
sudo apt-get purge pulseaudio
```Hope this helps get you on the right track.

---

### Post by Glix on 2009-07-07
glix@Ein:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
02:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

