---
title: "Wifi working on LiveCD but not after installing"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by zoulman on 2007-09-04
Hey all,

I decided to install Gutsy on my computer last night. I was delighted to see that everything worked perfectly when I booted on the Live CD (Even WI-FI with WPA encryption!).

Well after I had installed ubuntu and I logged in, I could no longer use the wireless connection.

So I decided to investigate (as best I knew how) and tried using iwconfig to see if my USB Hawking HWUG1 would show up. And indeed it did.

So, what could be wrong... well then I tried looking at ifconfig.

ifconfig did not show wlan0, so I tried ifconfig with the -a parameter and now it showed up. So from my limited knowledge I deducted that the interface must be down. So I tried sudo ifconfig wlan0 up.

It did not work and I received the error message:

**SIOCSIFFLAGS: No buffer space available**

And now I'm stuck. I have no idea what to do from here.

Please help.

---

### Post by zoulman on 2007-09-04
bump

---

### Post by kevdog on 2007-09-04
Im not sure why but your problem happens to a lot of people.  If you can post:

lshw -C network
lspci -nn

that would help.

---

### Post by qfb_ros on 2007-09-16
Hello!
Im having the same problems on a Laptop VAIO VGN - CR160F

----------------------------
ros@aeon:~$ sudo lshw -C network
[sudo] password for ros:
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:3b:ca:1b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:13:a9:f0:f5:e2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.123.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
------------------------------------
ros@aeon:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation Mobile SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4229] (rev 61)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
08:07.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:07.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:07.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
--------------------------------------------------------------

Any help would be great! Im runing Gutsy Tribe 5 and cant use WiFi
The nm-applet does detect several wifi networks, but cannot connect to anyone.

Thank you!

---

