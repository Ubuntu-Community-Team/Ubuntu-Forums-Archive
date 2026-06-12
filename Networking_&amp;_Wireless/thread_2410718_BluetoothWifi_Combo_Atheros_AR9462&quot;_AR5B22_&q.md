---
title: "Bluetooth/Wifi Combo Atheros AR9462&quot; AR5B22 &quot;  wifi works, no Bt device ?"
date: 2019-01-19
forum: Networking &amp; Wireless
---

### Post by tribbintripps on 2019-01-19
Lets get right to it. I blew the dust out of an old Gateway dx4870-ub318, and installed the latest ubuntu...everything seemed to be working much better than expected ! Than I installed steam and tried to link up to a bluetooth controller. Now I don't think this is a gaming pc by any means but that lead me to the realization that my pc is not recognizing at least half of the hardware I have installed. 

Installed : 03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc AR9462 Wireless Network Adapter [11ad:6621]
    Kernel driver in use: ath9k
    Kernel modules: ath9k

*(see below for full lspci -nnk ) *

Here is what I get with command:

  _$ lspci -nnk_
```

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
    Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [1025:063d]
    Kernel driver in use: ivb_uncore
    Kernel modules: ie31200_edac
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1025:8030]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family MEI Controller [1025:063d]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Acer Incorporated [ALI] 82579V Gigabit Network Connection [1025:8000]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family USB Enhanced Host Controller [1025:063d]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family High Definition Audio Controller [1025:063d]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 [8086:1e18] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family USB Enhanced Host Controller [1025:063d]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a4)
00:1f.0 ISA bridge [0601]: Intel Corporation B75 Express Chipset LPC Controller [8086:1e49] (rev 04)
    Subsystem: Acer Incorporated [ALI] B75 Express Chipset LPC Controller [1025:063d]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e02] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] [1025:063d]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family SMBus Controller [1025:063d]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 610] [10de:104a] (rev a1)
    Subsystem: eVga.com. Corp. GF119 [GeForce GT 610] [3842:3619]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GF119 HDMI Audio Controller [10de:0e08] (rev a1)
    Subsystem: eVga.com. Corp. GF119 HDMI Audio Controller [3842:3619]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
[B]03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc AR9462 Wireless Network Adapter [11ad:6621]
    Kernel driver in use: ath9k
    Kernel modules: ath9k[/B]

```

**_ISSUE:  Bluetooth is not working ( Although wifi is working great )_**

After days of going over all the google help I believe that I am not  skilled enough to tackle this issue on my own.  I have tried many  answers that at first had seamed promising until falling short of the  solution.  I have sense performed a complete reinstall of the latest  Ubuntu software and updates. I believe that I am ready to give this a  try with some support.

The issue I believe is related to a topic found [HERE]("https://askubuntu.com/a/791590") posted by [Pilot6]("https://askubuntu.com/users/167850/pilot6") 
```

 This problem exists because Atheros re-used the chip VID and PID.
  See this [bug report]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1542743")
  As a workaround you can patch the btusb.c module and change it form ath3k to Rome.
  I've built a DKMS package to fix this issue and uploaded it to my PPA.

  [https://launchpad.net/~hanipouspilot/+archive/ubuntu/bluetooth/+files/btusb-lp1542743-dkms_0.1_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/bluetooth/+files/btusb-lp1542743-dkms_0.1_all.deb)
  Install this deb and reboot. This should fix the issue. 
     

```

The bug report mentioned discusses a WORKAROUND FOR [0CF3:3004] DEVICE ONLY with kernel 4.4:
as well as FOR KERNEL 4.8 A WORKAROUND DKMS DEB

I am not sure if I am on the right or wrong path here but I believe the above is in face related .  any help would be apprechiated.  :)

---

### Post by wildmanne39 on 2019-01-19
*Thread moved to **Networking & Wireless for better support**.*

---

### Post by jeremy31 on 2019-01-19
Post results for ```
lsusb
```

---

### Post by tribbintripps on 2019-01-20
Please Forgive my late response. I will try to check back more frequently.

_**~$ lsusb**_
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0461:4e24 Primax Electronics, Ltd 
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 045e:02ea Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**_~$ rfkill_**

```

ID TYPE DEVICE      SOFT      HARD
 0 wlan phy0   unblocked unblocked
```

----------------------------------------------------------------------------------------------------------------------------------------------------------------------UPDATE
I have also tried connecting a usb BT dongle just to see if it would work and if It would appear. Turns out I may have a separate issue here. Is this somehow related ? Here is the requests after adding a usb bluetooth dongle ( as well as the internal ) 

**_~$ lsusb_**
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0461:4e24 Primax Electronics, Ltd 
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 008: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 001 Device 003: ID 045e:02ea Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[B][U]~$ rfkill
[/U][/B]ID TYPE      DEVICE      SOFT      HARD
 0 wlan      phy0   unblocked unblocked
 1 bluetooth hci0   unblocked unblocked


Bluetooth will not ture on under settings. At one point it was turning on and off however never stayed on . 
removed the dongle -- >>  Back to original issue .

---

