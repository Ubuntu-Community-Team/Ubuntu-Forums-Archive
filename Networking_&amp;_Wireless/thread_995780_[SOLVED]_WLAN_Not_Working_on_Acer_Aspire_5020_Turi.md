---
title: "[SOLVED] WLAN Not Working on Acer Aspire 5020 Turion 64"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by S_e_P_p on 2008-11-28
Hello,


I cannot get WLAN working on the laptop Acer Aspire 5020 with Ubuntu 8.10. It has a Broadcom 802.11g WLAN.

I tried already things like installing ACERHK and ACER-ACPI but couldn't find a solution(Make of acer-acpi crash and I supppose because its replaced by acer-wmi).

In Windows you have to install Acer Launch Manager to activate WLAN because the laptop has button on the front to start the wlan. These buttons are software controlled.

Happy to give you more information if possible. Just let me know.

Below are all information I have for my system:

**Processor Processor: **AMD Turion 64 mobile technology ML-34 / 1.8 GHz, Turion 64 mobile technology ML-34 / 1.8 GHz, 64-bit Computing: Yes

Features: PowerNow! technology, HyperTransport technology, PowerNow! technology, HyperTransport technology, AMD64 technology, integrated memory controller, Enhanced Virus Protection

**Chipset Type:** ATI Radeon Xpress 200, ATI Radeon Xpress 200M

Cache memory Type: L2 Cache Installed Size: 1 MB Storage controller Type: IDE

Optical storage Type: DVD±RW (+R double layer) - integrated, DVD±RW - integrated Card reader Type: 6 in 1 card reader Supported Flash Memory Cards: SD Memory Card, Memory Stick, Memory Stick PRO, MultiMediaCard, SmartMedia Card, xD-Picture Card

**Video**

Graphics Processor / Vendor: ATI Mobility Radeon X700 PCI Express, ATI Radeon X700 PCI Express, ATI Radeon X700 Video Memory: 128 MB, 256 MB Audio Audio Output: Sound card Audio Input: Microphone Compliant Standards: DirectSound

Input device(s) Type: Keyboard, touchpad, 4-way scroll button, Keyboard, touchpad, 4-way navigation button

Telecom Modem: Fax / Modem Max Transfer Rate: 56 Kbps Protocols & Specifications: ITU V.92

[B]Networking
[/B]
**Broadcom 802.11g WLAN, **Realtek RTL8169/8110 Gigabit LAN, Texas Instruments IEE 1394 Networking: Network adapter Wireless LAN Supported: Yes Data Link Protocol: Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g Remote Management Protocol: DMI 2.0 Compliant Standards: IEEE 802.11b, IEEE 802.11g, Wi-Fi CERTIFIED Features: Acer SignalUp Wireless NIC: Acer InviLink 802.11g


Thanks in advance for all your help!

Sebastian

---

### Post by Ayuthia on 2008-11-28
> **S_e_P_p said:**
> Hello,


I cannot get WLAN working on the laptop Acer Aspire 5020 with Ubuntu 8.10. It has a Broadcom 802.11g WLAN.

I tried already things like installing ACERHK and ACER-ACPI but couldn't find a solution(Make of acer-acpi crash and I supppose because its replaced by acer-wmi).

In Windows you have to install Acer Launch Manager to activate WLAN because the laptop has button on the front to start the wlan. These buttons are software controlled.

Happy to give you more information if possible. Just let me know.

Below are all information I have for my system:

**Processor Processor: **AMD Turion 64 mobile technology ML-34 / 1.8 GHz, Turion 64 mobile technology ML-34 / 1.8 GHz, 64-bit Computing: Yes

Features: PowerNow! technology, HyperTransport technology, PowerNow! technology, HyperTransport technology, AMD64 technology, integrated memory controller, Enhanced Virus Protection

**Chipset Type:** ATI Radeon Xpress 200, ATI Radeon Xpress 200M

Cache memory Type: L2 Cache Installed Size: 1 MB Storage controller Type: IDE

Optical storage Type: DVD±RW (+R double layer) - integrated, DVD±RW - integrated Card reader Type: 6 in 1 card reader Supported Flash Memory Cards: SD Memory Card, Memory Stick, Memory Stick PRO, MultiMediaCard, SmartMedia Card, xD-Picture Card

**Video**

Graphics Processor / Vendor: ATI Mobility Radeon X700 PCI Express, ATI Radeon X700 PCI Express, ATI Radeon X700 Video Memory: 128 MB, 256 MB Audio Audio Output: Sound card Audio Input: Microphone Compliant Standards: DirectSound

Input device(s) Type: Keyboard, touchpad, 4-way scroll button, Keyboard, touchpad, 4-way navigation button

Telecom Modem: Fax / Modem Max Transfer Rate: 56 Kbps Protocols & Specifications: ITU V.92

[B]Networking
[/B]
**Broadcom 802.11g WLAN, **Realtek RTL8169/8110 Gigabit LAN, Texas Instruments IEE 1394 Networking: Network adapter Wireless LAN Supported: Yes Data Link Protocol: Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g Remote Management Protocol: DMI 2.0 Compliant Standards: IEEE 802.11b, IEEE 802.11g, Wi-Fi CERTIFIED Features: Acer SignalUp Wireless NIC: Acer InviLink 802.11g


Thanks in advance for all your help!

Sebastian

Have you gone into System->Administration->Hardware Drivers?  There should be options there for the Broadcom b43 driver and/or Broadcom STA driver.  

The Broadcom b43 driver will need to have a working internet connection so that it can download some firmware that it needs to make the driver work.  If you don't have a working connection, here is a guide on what to download and install into Ubuntu:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

---

### Post by S_e_P_p on 2008-11-28
> **Ayuthia said:**
> Have you gone into System->Administration->Hardware Drivers?  There should be options there for the Broadcom b43 driver and/or Broadcom STA driver.  

The Broadcom b43 driver will need to have a working internet connection so that it can download some firmware that it needs to make the driver work.  If you don't have a working connection, here is a guide on what to download and install into Ubuntu:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

Hello Ayuthia,

Yes I did that. But still not working. I can't select the wlan or something like that because it looks like that it is still deactivated.

Thanks for helping

---

### Post by Ayuthia on 2008-11-28
> **S_e_P_p said:**
> Hello Ayuthia,

Yes I did that. But still not working. I can't select the wlan or something like that because it looks like that it is still deactivated.

Thanks for helping

Can you tell me which option you selected and if possible, can you post the results of:
```
lspci -nn
lshw -C network
```
I just want to see which model you have along with what driver the card is trying to use.

---

### Post by S_e_P_p on 2008-11-28
Hi, 

here are the requested information.

[PHP]sepp@sepp-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:06.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
	

sepp@sepp-laptop:~$ sudo lshw -C network
[sudo] password for sepp: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:fa:cf:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:20:32:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:05:1f:fa:18:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/PHP]

Thanks for help.

Sebastian

---

### Post by Ayuthia on 2008-11-28
It looks like the wireless card either does not have the firmware even though you tried to activate it or else it did not want to turn on.

Can you try the following:
```
sudo ifconfig wlan0 up
sudo iwlist scan

```This will try to turn on the card and scan for wireless sites

If it does not work, please post the results of:
```
dmesg|grep -e b43 -e wlan
aptitude search b43-fwcutter
```
This will help us see any error messages the b43 driver is getting along with checking to see if the firmware cutter application is installed.  If it is, the firmware is not installed, and you have a working internet connection you will need to run:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by S_e_P_p on 2008-11-29
Hello,

Yes the WLAN card wasn't started. Now im having Internet via Lan cable.

It looks like as the WLAN is ready now but I have to start the WLAN via the button on front of the laptop. But nothing happens if I press the button. Any Idea?

See details below after installation and restart:

```
sepp@sepp-laptop:~$ dmesg|grep -e b43 -e wlan
[    4.261778] b43-pci-bridge 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.658775] b43-phy0: Broadcom 4318 WLAN found
[   30.604514] input: b43-phy0 as /devices/virtual/input/input10
[   30.696096] firmware: requesting b43/ucode5.fw
[   30.778424] firmware: requesting b43/pcm5.fw
[   30.794783] firmware: requesting b43/b0g0initvals5.fw
[   30.805464] firmware: requesting b43/b0g0bsinitvals5.fw
[   30.932076] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.060441] Registered led device: b43-phy0::tx
[   31.061017] Registered led device: b43-phy0::rx
[   31.061498] Registered led device: b43-phy0::radio
[   31.624104] b43-phy0: Radio hardware status changed to DISABLED
[   31.716055] b43-phy0: Radio turned on by software
[   31.716070] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  102.904785] ADDRCONF(NETDEV_UP): wlan0: link is not ready
sepp@sepp-laptop:~$ aptitude search b43-fwcutter
i   b43-fwcutter                    - Utility for extracting Broadcom 43xx firmw
sepp@sepp-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for sepp: 
sepp@sepp-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


```

And again the other:

```
sepp@sepp-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:06.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)

```

```
sepp@sepp-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:fa:cf:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.27 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:20:32:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:10:11:de:f1:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Thanks for helping!!!

Sebastian

---

### Post by RecoilUK on 2008-11-29
Hi

Try this ...

to turn it on.```
echo 1 > /sys/devices/platform/acer-wmi/wireless
``` 
to turn it off.
```
echo 0 > /sys/devices/platform/acer-wmi/wireless
``` 
I,m currently searching for a way to use the button, if I have any success i,ll let you know.

Hope it helps.

---

### Post by S_e_P_p on 2008-11-29
It's working now! Thank you very much. Amazing. I spent arround 8 hours to get it working. 

The problem was that I hadn't done this:
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

and afterwards the activation through this:
echo 1 > /sys/devices/platform/acer-wmi/wireless

Thank you both for helping me. This is really aprecciated!

Greetings and a nice weekend.

Sebastian

---

