---
title: "Ethernet/ wired connection to router?"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by VietxHieu on 2007-10-09
Hey guys sorry but i'm new and still trying to figure some things out ^^ one thing i havent figured out is that why isn't my Ethernet/wired connection working... Specs

MSI 925X Neo Platinum Edition

Ram 2 gig

Using Ubuntu: Feisty Fawn 7.04 GNU/LINUX

The slot for the ethernet cord is placed in the right place.

on a different computer in my household i did everything the same as for my desktop, but still the laptop can have wired internet....
I dont know if i need to configure anything? because shouldn't it be able to recognize it on it's own?
Please help me, i'm using a dinky USB internet thing :lolflag: and it get's annoying because my router is like a foot away from the computer yet it loses connection continuesly, i believe with a live connection to my router this would stop that from happening ^^ Thanks for reading.
Much Appreciated
Hieu.

---

### Post by noob12 on 2007-10-10
Please post the output of these commands.  This would tell us what the actual device is and what driver is associated to the device if any.

```

lspci -nn

sudo lshw -C network

```

---

### Post by VietxHieu on 2007-10-10
00:00.0 Host bridge [0600]: Intel Corporation 82925X/XE Memory Controller Hub [8086:2584] (rev 04)

00:01.0 PCI bridge [0604]: Intel Corporation 82925X/XE PCI Express Root Port [8086:2585] (rev 04)

00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)

00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)

00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)

00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)

00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)

00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)

00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)

00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)

00:1f.2 IDE interface [0101]: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller [8086:2652] (rev 03)

00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)

01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:016a] (rev a1)

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677]

03:01.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)

03:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46)

03:04.0 IDE interface [0101]: VIA Technologies, Inc. VT6410 ATA133 RAID controller [1106:3164] (rev 06)

03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller [8086:1065] (rev 03)



Second command:

*-network UNCLAIMED     

       description: Ethernet controller

       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@02:00.0

       version: 00

       width: 64 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=0

       resources: iomemory:d0000000-d000ffff irq:16

  *-network:0 DISABLED

       description: Wireless interface

       product: BCM4303 802.11b Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 1

       bus info: pci@03:01.0

       logical name: eth0

       version: 02

       serial: 00:06:25:1c:52:42

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b

       resources: iomemory:d0100000-d0101fff irq:21

  *-network:1 UNCLAIMED

       description: Ethernet controller

       product: 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@03:08.0

       version: 03

       width: 32 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=32 maxlatency=56 mingnt=8

       resources: iomemory:d0103000-d0103fff ioport:d600-d63f irq:20

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:0f:b5:dc:90:48

       capabilities: ethernet physical wireless

       configuration: broadcast=yes ip=192.168.1.122 multicast=yes wireless=IEEE 802.11g


There ya go, Thanks for helping

---

### Post by noob12 on 2007-10-10
Here's what we see looking at the two unclaimed wired cards.

This one:
```

03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller [8086:1065] (rev 03)

```
should be covered by the **e100** driver in Feisty.   We need to see why it isn't being claimed.
A common problem is the eeprom checksum failing.  We should be albe to get around this by adding an option when loading the driver.  We need to check the dmesg to see if this is in fact the cause.

This one:
```

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677]

```
should be covered by the **tg3** driver in Feisty.

The fact that both are unclaimed suggests that there might a more fundamental problem during the boot.  In both cases we should see more clues in the output of **dmesg**.

Sp please post the output of the command ```
dmesg
```

---

### Post by VietxHieu on 2007-10-10
Whow really long results...

r load failed.
[ 3665.989776] wlan0: starting scan
[ 3666.648496] wlan0: scan completed
[ 3768.153128] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 3786.544033] wlan0: starting scan
[ 3787.206692] wlan0: scan completed
[ 3863.753125] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 3892.918138] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 3907.097001] wlan0: starting scan
[ 3907.759732] wlan0: scan completed
[ 4017.062407] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4027.640670] wlan0: starting scan
[ 4028.299467] wlan0: scan completed
[ 4140.679733] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4148.181265] wlan0: starting scan
[ 4148.839948] wlan0: scan completed
[ 4250.297481] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4265.527222] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4268.736138] wlan0: starting scan
[ 4269.395175] wlan0: scan completed
[ 4389.292366] wlan0: starting scan
[ 4389.952011] wlan0: scan completed
[ 4390.358688] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4509.833524] wlan0: starting scan
[ 4510.492571] wlan0: scan completed
[ 4513.627460] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4586.892993] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4630.380187] wlan0: starting scan
[ 4631.037308] wlan0: scan completed
[ 4638.352945] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4750.935555] wlan0: starting scan
[ 4751.593864] wlan0: scan completed
[ 4762.983334] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4871.481375] wlan0: starting scan
[ 4872.140354] wlan0: scan completed
[ 4875.578272] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4886.848251] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 4992.018211] wlan0: starting scan
[ 4992.677397] wlan0: scan completed
[ 5010.878911] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5112.557983] wlan0: starting scan
[ 5113.217210] wlan0: scan completed
[ 5135.400892] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5233.112855] wlan0: starting scan
[ 5233.771894] wlan0: scan completed
[ 5243.114384] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5259.332331] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5353.659058] wlan0: starting scan
[ 5354.318136] wlan0: scan completed
[ 5382.780528] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5474.206800] wlan0: starting scan
[ 5474.865799] wlan0: scan completed
[ 5475.842190] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5507.449442] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5594.753955] wlan0: starting scan
[ 5595.416807] wlan0: scan completed
[ 5631.483588] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5715.307869] wlan0: starting scan
[ 5715.966839] wlan0: scan completed
[ 5755.062694] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5767.491149] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5835.861334] wlan0: starting scan
[ 5836.524276] wlan0: scan completed
[ 5879.844789] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 5956.416144] wlan0: starting scan
[ 5957.078904] wlan0: scan completed
[ 6003.990837] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6076.960006] wlan0: starting scan
[ 6077.619014] wlan0: scan completed
[ 6127.683253] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6164.024384] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6197.519615] wlan0: starting scan
[ 6198.178515] wlan0: scan completed
[ 6252.571451] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6318.065606] wlan0: starting scan
[ 6318.728666] wlan0: scan completed
[ 6376.813838] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6438.621599] wlan0: starting scan
[ 6439.280579] wlan0: scan completed
[ 6500.585557] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6559.168739] wlan0: starting scan
[ 6559.831889] wlan0: scan completed
[ 6621.478661] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6625.529025] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6679.727807] wlan0: starting scan
[ 6680.386920] wlan0: scan completed
[ 6749.900405] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6800.283328] wlan0: starting scan
[ 6800.950444] wlan0: scan completed
[ 6850.207343] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6873.763269] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 6920.830722] wlan0: starting scan
[ 6921.489808] wlan0: scan completed
[ 6997.975942] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7041.375562] wlan0: starting scan
[ 7042.038727] wlan0: scan completed
[ 7089.922212] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7122.509894] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7161.932077] wlan0: starting scan
[ 7162.591178] wlan0: scan completed
[ 7246.425111] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7282.486803] wlan0: starting scan
[ 7283.149782] wlan0: scan completed
[ 7369.845218] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7375.584019] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7403.040189] wlan0: starting scan
[ 7403.699324] wlan0: scan completed
[ 7494.519444] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7523.581805] wlan0: starting scan
[ 7524.240395] wlan0: scan completed
[ 7618.605453] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7644.135434] wlan0: starting scan
[ 7644.794190] wlan0: scan completed
[ 7740.153034] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7742.185593] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7764.692508] wlan0: starting scan
[ 7765.355264] wlan0: scan completed
[ 7866.949777] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 7885.230069] wlan0: starting scan
[ 7885.888668] wlan0: scan completed
[ 7991.125173] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8005.782794] wlan0: starting scan
[ 8006.441474] wlan0: scan completed
[ 8114.783908] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8126.345785] wlan0: starting scan
[ 8127.008422] wlan0: scan completed
[ 8163.646198] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8239.652351] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8246.911517] wlan0: starting scan
[ 8247.570127] wlan0: scan completed
[ 8363.973169] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8367.448392] wlan0: starting scan
[ 8368.107161] wlan0: scan completed
[ 8395.371118] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8487.727336] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8488.001734] wlan0: starting scan
[ 8488.660351] wlan0: scan completed
[ 8608.566758] wlan0: starting scan
[ 8609.225480] wlan0: scan completed
[ 8612.683907] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8729.117858] wlan0: starting scan
[ 8729.776548] wlan0: scan completed
[ 8737.029987] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8843.840839] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8849.665683] wlan0: starting scan
[ 8850.324773] wlan0: scan completed
[ 8860.884986] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 8970.212243] wlan0: starting scan
[ 8970.875232] wlan0: scan completed
[ 8985.206513] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9090.772371] wlan0: starting scan
[ 9091.431336] wlan0: scan completed
[ 9109.688531] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9171.451163] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9211.334404] wlan0: starting scan
[ 9211.993539] wlan0: scan completed
[ 9233.666638] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9331.884904] wlan0: starting scan
[ 9332.544076] wlan0: scan completed
[ 9357.127788] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9452.422524] wlan0: starting scan
[ 9453.080397] wlan0: scan completed
[ 9467.098853] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9481.800561] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9572.961456] wlan0: starting scan
[ 9573.624372] wlan0: scan completed
[ 9605.865667] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9693.513951] wlan0: starting scan
[ 9694.177106] wlan0: scan completed
[ 9729.466949] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9814.065874] wlan0: starting scan
[ 9814.725869] wlan0: scan completed
[ 9854.204301] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9934.614345] wlan0: starting scan
[ 9935.274570] wlan0: scan completed
[ 9942.556007] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[ 9978.395280] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10055.165889] wlan0: starting scan
[10055.825999] wlan0: scan completed
[10101.899204] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10175.710538] wlan0: starting scan
[10176.370407] wlan0: scan completed
[10177.316111] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10226.742977] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10296.263919] wlan0: starting scan
[10296.925706] wlan0: scan completed
[10351.037110] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10416.799947] wlan0: starting scan
[10417.460031] wlan0: scan completed
[10474.793952] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10475.707424] wiphy1: unknown frame RXed (0x1e)
[10481.381148] wlan0: No ProbeResp from current AP 00:14:bf:36:5d:1f - assume out of range
[10481.485669] wlan0: Initial auth_alg=0
[10481.485680] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10481.485729] wlan0: Initial auth_alg=0
[10481.485734] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10481.485785] wlan0: Initial auth_alg=0
[10481.485789] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10481.685930] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10481.886159] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10482.086239] wlan0: authentication with AP 00:14:bf:36:5d:1f timed out
[10486.486161] wlan0: Initial auth_alg=0
[10486.486171] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10486.486222] wlan0: Initial auth_alg=0
[10486.486228] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10486.486285] wlan0: Initial auth_alg=0
[10486.486290] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10486.685987] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10486.882000] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10487.082056] wlan0: authentication with AP 00:14:bf:36:5d:1f timed out
[10490.383737] wlan0: starting scan
[10493.628962] usb 1-1: USB disconnect, address 5
[10494.369877] usb 1-1: new high speed USB device using ehci_hcd and address 6
[10494.507444] usb 1-1: configuration #1 chosen from 1 choice
[10494.551239] p54: LM86 firmware
[10494.987032] wmaster0: Selected rate control algorithm 'simple'
[10494.987181] wiphy2: hwaddr 00:0f:b5:dc:90:48, isl3887
[10495.078804] wmaster0: Does not support passive scan, disabled
[10495.103373] wlan0: starting scan
[10495.764317] wlan0: scan completed
[10515.769796] wlan0: starting scan
[10516.430325] wlan0: scan completed
[10536.445140] wlan0: starting scan
[10537.105212] wlan0: scan completed
[10557.128806] wlan0: starting scan
[10557.792714] wlan0: scan completed
[10562.843409] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10577.790677] wlan0: starting scan
[10578.451064] wlan0: scan completed
[10598.456825] wlan0: starting scan
[10599.116814] wlan0: scan completed
[10599.733057] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10619.137800] wlan0: starting scan
[10619.796441] wlan0: scan completed
[10635.825416] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10640.845420] wlan0: Initial auth_alg=0
[10640.845429] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10640.845475] wlan0: Initial auth_alg=0
[10640.845479] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10640.845528] wlan0: Initial auth_alg=0
[10640.845532] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10640.851288] wlan0: RX authentication from 00:14:bf:36:5d:1f (alg=0 transaction=2 status=0)
[10640.851296] wlan0: authenticated
[10640.851300] wlan0: associate with AP 00:14:bf:36:5d:1f
[10640.852154] wlan0: authentication frame received from 00:14:bf:36:5d:1f, but not in authenticate state - ignored
[10640.855772] wlan0: authentication frame received from 00:14:bf:36:5d:1f, but not in authenticate state - ignored
[10640.856906] wlan0: RX AssocResp from 00:14:bf:36:5d:1f (capab=0x411 status=0 aid=1)
[10640.856912] wlan0: associated
[10655.634215] wlan0: no IPv6 routers present
[10724.899734] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10740.459997] wlan0: starting scan
[10741.120091] wlan0: scan completed
[10748.840003] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10761.121446] wlan0: starting scan
[10761.781939] wlan0: scan completed
[10781.758594] wlan0: No ProbeResp from current AP 00:14:bf:36:5d:1f - assume out of range
[10781.862908] wlan0: Initial auth_alg=0
[10781.862916] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10781.862966] wlan0: Initial auth_alg=0
[10781.862972] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10781.863020] wlan0: Initial auth_alg=0
[10781.863025] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10782.063264] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10782.263816] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10782.464178] wlan0: authentication with AP 00:14:bf:36:5d:1f timed out
[10786.859653] wlan0: Initial auth_alg=0
[10786.859662] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10786.859708] wlan0: Initial auth_alg=0
[10786.859713] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10786.859764] wlan0: Initial auth_alg=0
[10786.859768] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10787.059386] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10787.259422] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[10787.459443] wlan0: authentication with AP 00:14:bf:36:5d:1f timed out
[10790.758849] wlan0: starting scan
[10793.323941] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10794.422355] usb 1-1: USB disconnect, address 6
[10794.801917] usb 1-1: new high speed USB device using ehci_hcd and address 7
[10794.938949] usb 1-1: configuration #1 chosen from 1 choice
[10794.980363] p54: LM86 firmware
[10795.416151] wmaster0: Selected rate control algorithm 'simple'
[10795.416296] wiphy3: hwaddr 00:0f:b5:dc:90:48, isl3887
[10795.596575] wmaster0: Does not support passive scan, disabled
[10795.618145] wlan0: starting scan
[10796.282071] wlan0: scan completed
[10816.294096] wlan0: starting scan
[10816.954154] wlan0: scan completed
[10836.967881] wlan0: starting scan
[10837.628058] wlan0: scan completed
[10857.630455] wlan0: starting scan
[10858.290441] wlan0: scan completed
[10873.737647] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[10878.308193] wlan0: starting scan
[10878.968415] wlan0: scan completed
[10898.977762] wlan0: starting scan
[10899.637590] wlan0: scan completed
[10919.636363] wlan0: starting scan
[10920.297365] wlan0: scan completed
[10997.911140] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11040.180068] wlan0: starting scan
[11040.840885] wlan0: scan completed
[11121.648070] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11160.725344] wlan0: starting scan
[11161.385276] wlan0: scan completed
[11226.809476] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11246.510162] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11281.282316] wlan0: starting scan
[11281.942316] wlan0: scan completed
[11370.783498] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11401.847452] wlan0: starting scan
[11402.507631] wlan0: scan completed
[11494.733966] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11522.391704] wlan0: starting scan
[11523.051822] wlan0: scan completed
[11600.383764] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11619.692096] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11642.937732] wlan0: starting scan
[11643.600656] wlan0: scan completed
[11744.080875] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11763.481418] wlan0: starting scan
[11764.142181] wlan0: scan completed
[11867.893880] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11878.034498] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[11884.042872] wlan0: starting scan
[11884.702890] wlan0: scan completed
[11991.857456] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12004.589293] wlan0: starting scan
[12005.253246] wlan0: scan completed
[12116.504514] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12125.129790] wlan0: starting scan
[12125.790029] wlan0: scan completed
[12240.243877] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12245.669418] wlan0: starting scan
[12246.329596] wlan0: scan completed
[12247.649556] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12363.837619] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12366.231651] wlan0: starting scan
[12366.891976] wlan0: scan completed
[12452.976890] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12455.333633] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12457.998158] wlan0: Initial auth_alg=0
[12457.998167] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[12457.998232] wlan0: Initial auth_alg=0
[12457.998237] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[12457.998287] wlan0: Initial auth_alg=0
[12457.998291] wlan0: authenticate with AP 00:14:bf:36:5d:1f
[12458.004101] wlan0: RX authentication from 00:14:bf:36:5d:1f (alg=0 transaction=2 status=0)
[12458.004107] wlan0: authenticated
[12458.004112] wlan0: associate with AP 00:14:bf:36:5d:1f
[12458.005715] wlan0: authentication frame received from 00:14:bf:36:5d:1f, but not in authenticate state - ignored
[12458.006716] wlan0: authentication frame received from 00:14:bf:36:5d:1f, but not in authenticate state - ignored
[12458.007713] wlan0: RX AssocResp from 00:14:bf:36:5d:1f (capab=0x411 status=0 aid=1)
[12458.007718] wlan0: associated
[12472.523279] wlan0: no IPv6 routers present
[12486.803079] wlan0: starting scan
[12487.466181] wlan0: scan completed
[12488.582003] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12507.474028] wlan0: starting scan
[12508.133053] wlan0: scan completed
[12512.792615] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12528.150783] wlan0: starting scan
[12528.813814] wlan0: scan completed
[12537.215183] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12548.841064] wlan0: starting scan
[12549.500012] wlan0: scan completed
[12561.569267] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12569.515432] wlan0: starting scan
[12570.178374] wlan0: scan completed
[12585.159625] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12590.200214] wlan0: starting scan
[12590.859603] wlan0: scan completed
[12709.781121] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12710.811580] wlan0: starting scan
[12711.474332] wlan0: scan completed
[12831.415508] wlan0: starting scan
[12832.080548] wlan0: scan completed
[12833.787738] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12863.043758] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[12951.976656] wlan0: starting scan
[12952.638635] wlan0: scan completed
[12957.467904] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

---

### Post by VietxHieu on 2007-10-11
so how would i configure it to be recognize and/or take one out that isnt needed?

---

### Post by noob12 on 2007-10-11
Sorry, but I should have mentioned that you need to run the **dmesg** command right after you boot in order to capture the recent kernel log history.  The output you grabbed missed all of the initial boot messages.

---

### Post by VietxHieu on 2007-10-25
[    0.000000]   DMA             0 ->     4096

[    0.000000]   Normal       4096 ->   229376

[    0.000000]   HighMem    229376 ->   524272

[    0.000000] early_node_map[1] active PFN ranges

[    0.000000]     0 :       0 ->   524272

[    0.000000] On node 0 totalpages: 524272

[    0.000000]   DMA zone: 32 pages used for memmap

[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

[    0.000000]   Normal zone: 1760 pages used for memmap

[    0.000000]   Normal zone: 223520 pages, LIFO batch:31

[    0.000000]   HighMem zone: 2303 pages used for memmap

[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31

[    0.000000] DMI 2.2 present.

[    0.000000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f7610

[    0.000000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3040

[    0.000000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff30c0

[    0.000000] ACPI: MCFG (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff7740

[    0.000000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff7640

[    0.000000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000

[    0.000000] ACPI: PM-Timer IO Port: 0x408

[    0.000000] ACPI: Local APIC address 0xfee00000

[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

[    0.000000] Processor #0 15:4 APIC version 20

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)

[    0.000000] Processor #1 15:4 APIC version 20

[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)

[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])

[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])

[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

[    0.000000] ACPI: IRQ0 used by override.

[    0.000000] ACPI: IRQ2 used by override.

[    0.000000] ACPI: IRQ9 used by override.

[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.000000] Using ACPI (MADT) for SMP configuration information

[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)

[    0.000000] Detected 2999.430 MHz processor.

[   15.385047] Built 1 zonelists.  Total pages: 520177

[   15.385051] Kernel command line: root=UUID=a0f0e5ed-b448-4b68-ac2b-e7a6fe26355f ro quiet splash

[   15.385202] mapped APIC to ffffd000 (fee00000)

[   15.385205] mapped IOAPIC to ffffc000 (fec00000)

[   15.385207] Enabling fast FPU save and restore... done.

[   15.385211] Enabling unmasked SIMD FPU exception support... done.

[   15.385219] Initializing CPU#0

[   15.385278] PID hash table entries: 4096 (order: 12, 16384 bytes)

[   15.387458] Console: colour VGA+ 80x25

[   15.387829] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

[   15.388187] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

[   15.463704] Memory: 2068012k/2097088k available (1993k kernel code, 27724k reserved, 900k data, 328k init, 1179584k highmem)

[   15.463715] virtual kernel memory layout:

[   15.463716]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

[   15.463717]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[   15.463718]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

[   15.463719]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

[   15.463720]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)

[   15.463721]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)

[   15.463723]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)

[   15.463726] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[   15.541097] Calibrating delay using timer specific routine.. 6003.75 BogoMIPS (lpj=12007505)

[   15.541138] Security Framework v1.0.0 initialized

[   15.541144] SELinux:  Disabled at boot.

[   15.541160] Mount-cache hash table entries: 512

[   15.541297] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001

[   15.541305] monitor/mwait feature present.

[   15.541307] using mwait in idle threads.

[   15.541314] CPU: Trace cache: 12K uops, L1 D cache: 16K

[   15.541317] CPU: L2 cache: 1024K

[   15.541319] CPU: Physical Processor ID: 0

[   15.541321] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000641d 00000000 00000001

[   15.541332] Compat vDSO mapped to ffffe000.

[   15.541336] Remapping vsyscall page to ffffe000

[   15.541351] Checking 'hlt' instruction... OK.

[   15.557183] SMP alternatives: switching to UP code

[   15.557582] Early unpacking initramfs... done

[   15.827656] ACPI: Core revision 20060707

[   15.833638] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

[   15.841524] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09

[   15.841547] SMP alternatives: switching to SMP code

[   15.841658] Booting processor 1/1 eip 3000

[   15.851955] Initializing CPU#1

[   15.932623] Calibrating delay using timer specific routine.. 5998.76 BogoMIPS (lpj=11997535)

[   15.932633] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001

[   15.932640] monitor/mwait feature present.

[   15.932647] CPU: Trace cache: 12K uops, L1 D cache: 16K

[   15.932649] CPU: L2 cache: 1024K

[   15.932652] CPU: Physical Processor ID: 0

[   15.932654] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000641d 00000000 00000001

[   15.932927] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09

[   15.932969] Total of 2 processors activated (12002.52 BogoMIPS).

[   15.933117] ENABLING IO-APIC IRQs

[   15.933297] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

[   16.080454] checking TSC synchronization across 2 CPUs: passed.

[    0.003994] Brought up 2 CPUs

[    0.098631] migration_cost=114

[    0.098911] Booting paravirtualized kernel on bare hardware

[    0.098988] Time: 23:07:32  Date: 09/25/107

[    0.099018] NET: Registered protocol family 16

[    0.099109] EISA bus registered

[    0.099115] ACPI: bus type pci registered

[    0.124665] PCI: PCI BIOS revision 3.00 entry at 0xfbad0, last bus=3

[    0.124668] PCI: Using configuration type 1

[    0.124670] Setting up standard PCI resources

[    0.140448] ACPI: Interpreter enabled

[    0.140452] ACPI: Using IOAPIC for interrupt routing

[    0.141069] ACPI: PCI Root Bridge [PCI0] (0000:00)

[    0.141073] PCI: Probing PCI hardware (bus 00)

[    0.141747] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO

[    0.141751] PCI quirk: region 0480-04bf claimed by ICH6 GPIO

[    0.141994] Boot video device is 0000:01:00.0

[    0.142432] PCI: Firmware left 0000:03:08.0 e100 interrupts enabled, disabling

[    0.142512] PCI: Transparent bridge - 0000:00:1e.0

[    0.142561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.152675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]

[    0.153298] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]

[    0.156994] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)

[    0.157264] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)

[    0.157531] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)

[    0.157802] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)

[    0.158074] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)

[    0.158344] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

[    0.158612] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

[    0.158883] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)

[    0.159187] Linux Plug and Play Support v0.97 (c) Adam Belay

[    0.159199] pnp: PnP ACPI init

[    0.162714] pnp: PnP ACPI: found 14 devices

[    0.162720] PnPBIOS: Disabled by ACPI PNP

[    0.162776] PCI: Using ACPI for IRQ routing

[    0.162780] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

[    0.238323] NET: Registered protocol family 8

[    0.238325] NET: Registered protocol family 20

[    0.238717] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved

[    0.239058] PCI: Bridge: 0000:00:01.0

[    0.239061]   IO window: disabled.

[    0.239065]   MEM window: b0000000-cfffffff

[    0.239069]   PREFETCH window: 88000000-880fffff

[    0.239073] PCI: Bridge: 0000:00:1c.0

[    0.239074]   IO window: disabled.

[    0.239079]   MEM window: d0000000-d00fffff

[    0.239083]   PREFETCH window: disabled.

[    0.239088] PCI: Bridge: 0000:00:1e.0

[    0.239091]   IO window: d000-dfff

[    0.239096]   MEM window: d0100000-d01fffff

[    0.239100]   PREFETCH window: disabled.

[    0.239117] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16

[    0.239123] PCI: Setting latency timer of device 0000:00:01.0 to 64

[    0.239142] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16

[    0.239148] PCI: Setting latency timer of device 0000:00:1c.0 to 64

[    0.239159] PCI: Setting latency timer of device 0000:00:1e.0 to 64

[    0.239190] NET: Registered protocol family 2

[    0.283901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.284037] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.284613] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.284978] TCP: Hash tables configured (established 131072 bind 65536)

[    0.284982] TCP reno registered

[    0.300042] checking if image is initramfs... it is

[    0.833241] Freeing initrd memory: 6785k freed

[    0.833857] audit: initializing netlink socket (disabled)

[    0.833874] audit(1193353652.604:1): initialized

[    0.833978] highmem bounce pool size: 64 pages

[    0.834072] VFS: Disk quotas dquot_6.5.1

[    0.834092] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    0.834140] io scheduler noop registered

[    0.834144] io scheduler anticipatory registered

[    0.834146] io scheduler deadline registered

[    0.834159] io scheduler cfq registered (default)

[    0.834388] PCI: Setting latency timer of device 0000:00:01.0 to 64

[    0.834430] assign_interrupt_mode Found MSI capability

[    0.834433] Allocate Port Service[0000:00:01.0:pcie00]

[    0.834532] PCI: Setting latency timer of device 0000:00:1c.0 to 64

[    0.834576] assign_interrupt_mode Found MSI capability

[    0.834579] Allocate Port Service[0000:00:1c.0:pcie00]

[    0.834616] Allocate Port Service[0000:00:1c.0:pcie02]

[    0.834794] isapnp: Scanning for PnP cards...

[    1.186114] isapnp: No Plug & Play device found

[    1.213064] Real Time Clock Driver v1.12ac

[    1.213121] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[    1.213241] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    1.213891] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    1.214133] mice: PS/2 mouse device common for all mice

[    1.214793] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[    1.214947] input: Macintosh mouse button emulation as /class/input/input0

[    1.214991] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

[    1.214996] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

[    1.215201] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1

[    1.215204] PNP: PS/2 controller doesn't have AUX irq; using default 12

[    1.217534] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.217541] serio: i8042 AUX port at 0x60,0x64 irq 12

[    1.217666] EISA: Probing bus 0 at eisa.0

[    1.217697] EISA: Detected 0 cards.

[    1.247744] TCP cubic registered

[    1.247753] NET: Registered protocol family 1

[    1.247774] Starting balanced_irq

[    1.247783] Using IPI No-Shortcut mode

[    1.247862] input: AT Translated Set 2 keyboard as /class/input/input1

[    1.247944] ACPI: (supports S0 S1 S4 S5)

[    1.248005]   Magic number: 11:409:151

[    1.248059]   hash matches device ttyp5

[    1.248324] Freeing unused kernel memory: 328k freed

[    1.250484] Time: tsc clocksource has been installed.

[    2.465511] Capability LSM initialized

[    2.502693] ACPI: Fan [FAN] (on)

[    2.506952] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]

[    2.506963] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]

[    2.508618] ACPI: Thermal Zone [THRM] (0 C)

[    2.950612] usbcore: registered new interface driver usbfs

[    2.950644] usbcore: registered new interface driver hub

[    2.956415] usbcore: registered new device driver usb

[    2.957735] USB Universal Host Controller Interface driver v3.0

[    2.957790] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17

[    2.957804] PCI: Setting latency timer of device 0000:00:1d.0 to 64

[    2.957811] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    2.957967] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

[    2.957997] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e300

[    2.958141] usb usb1: configuration #1 chosen from 1 choice

[    2.958177] hub 1-0:1.0: USB hub found

[    2.958186] hub 1-0:1.0: 2 ports detected

[    3.060997] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI

[    3.061002] e100: Copyright(c) 1999-2006 Intel Corporation

[    3.061885] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18

[    3.061899] PCI: Setting latency timer of device 0000:00:1d.1 to 64

[    3.061904] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    3.061935] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

[    3.061966] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e000

[    3.062089] usb usb2: configuration #1 chosen from 1 choice

[    3.062126] hub 2-0:1.0: USB hub found

[    3.062135] hub 2-0:1.0: 2 ports detected

[    3.102518] ieee1394: Initialized config rom entry `ip1394'

[    3.165738] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19

[    3.165752] PCI: Setting latency timer of device 0000:00:1d.2 to 64

[    3.165758] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    3.165794] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

[    3.165828] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e100

[    3.165958] usb usb3: configuration #1 chosen from 1 choice

[    3.165995] hub 3-0:1.0: USB hub found

[    3.166004] hub 3-0:1.0: 2 ports detected

[    3.213276] FDC 0 is a post-1991 82077

[    3.269916] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16

[    3.269932] PCI: Setting latency timer of device 0000:00:1d.3 to 64

[    3.269938] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[    3.269971] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4

[    3.270003] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200

[    3.270143] usb usb4: configuration #1 chosen from 1 choice

[    3.270188] hub 4-0:1.0: USB hub found

[    3.270198] hub 4-0:1.0: 2 ports detected

[    3.301879] usb 1-1: new low speed USB device using uhci_hcd and address 2

[    3.374299] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 20

[    3.397401] e100: 0000:03:08.0: e100_eeprom_load: EEPROM corrupted

[    3.397429] ACPI: PCI interrupt for device 0000:03:08.0 disabled

[    3.414192] e100: probe of 0000:03:08.0 failed with error -11

[    3.414528] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 18

[    3.470390] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d0102000-d01027ff]  Max Packet=[65536]  IR/IT contexts=[4/4]

[    3.477373] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes

[    3.477628] SCSI subsystem initialized

[    3.478140] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17

[    3.478186] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[    3.478202] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    3.478269] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[    3.478307] PCI: cache line size of 128 is not supported by device 0000:00:1d.7

[    3.478315] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd0204000

[    3.482206] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    3.482313] usb usb5: configuration #1 chosen from 1 choice

[    3.482354] hub 5-0:1.0: USB hub found

[    3.482362] hub 5-0:1.0: 8 ports detected

[    3.486151] libata version 2.20 loaded.

[    3.497372] usb 1-1: device descriptor read/all, error -71

[    3.586672] VP_IDE: IDE controller at PCI slot 0000:03:04.0

[    3.586696] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 20

[    3.586711] VP_IDE: chipset revision 6

[    3.586726] VP_IDE: VIA vt6410 (rev 06) IDE UDMA133 controller on pci0000:03:04.0

[    3.586730] VP_IDE: 100% native mode on irq 20

[    3.586738]     ide0: BM-DMA at 0xd500-0xd507, BIOS settings: hda:pio, hdb:pio

[    3.586754]     ide1: BM-DMA at 0xd508-0xd50f, BIOS settings: hdc:pio, hdd:pio

[    3.586765] Probing IDE interface ide0...

[    4.155712] Probing IDE interface ide1...

[    4.231885] usb 5-5: new high speed USB device using ehci_hcd and address 3

[    4.368719] usb 5-5: configuration #1 chosen from 1 choice

[    4.608950] usb 5-6: new high speed USB device using ehci_hcd and address 4

[    4.745373] usb 5-6: configuration #1 chosen from 1 choice

[    4.745783] usbcore: registered new interface driver libusual

[    4.749588] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[ffffffffffffffff]

[    4.752062] Initializing USB Mass Storage driver...

[    4.893828] hdc: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive

[    4.985948] usb 1-1: new low speed USB device using uhci_hcd and address 4

[    5.141387] usb 1-1: configuration #1 chosen from 1 choice

[    5.144510] scsi0 : SCSI emulation for USB Mass Storage devices

[    5.144583] usb-storage: device found at 3

[    5.144586] usb-storage: waiting for device to settle before scanning

[    5.144614] usbcore: registered new interface driver usb-storage

[    5.144619] USB Mass Storage support registered.

[    5.155400] usbcore: registered new interface driver hiddev

[    5.168353] input: HID 062a:0000 as /class/input/input2

[    5.168385] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.0-1

[    5.168402] usbcore: registered new interface driver usbhid

[    5.168406] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

[    5.563922] ide1 at 0xd300-0xd307,0xd402 on irq 20

[    5.564683] tg3.c:v3.72.1 (January 8, 2007)

[    5.564703] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16

[    5.564714] PCI: Setting latency timer of device 0000:02:00.0 to 64

[    6.378786] tg3: Could not obtain valid ethernet address, aborting.

[    6.378810] ACPI: PCI interrupt for device 0000:02:00.0 disabled

[    6.378817] tg3: probe of 0000:02:00.0 failed with error -22

[    6.381878] ata_piix 0000:00:1f.1: version 2.10ac1

[    6.381904] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19

[    6.381928] PCI: Setting latency timer of device 0000:00:1f.1 to 64

[    6.385191] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14

[    6.386181] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15

[    6.386211] scsi1 : ata_piix

[    6.393059] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)

[    6.393074] Uniform CD-ROM driver Revision: 3.20

[    6.551327] ata1.00: ata_hpa_resize 1: sectors = 60074784, hpa_sectors = 60074784

[    6.551332] ata1.00: ATA-4: WDC WD307AA, 05.05B05, max UDMA/66

[    6.551335] ata1.00: 60074784 sectors, multi 16: LBA 

[    6.551340] ata1.00: limited to UDMA/33 due to 40-wire cable

[    6.563321] ata1.00: ata_hpa_resize 1: sectors = 60074784, hpa_sectors = 60074784

[    6.563325] ata1.00: configured for UDMA/33

[    6.563335] scsi2 : ata_piix

[    6.728911] ATA: abnormal status 0x7F on port 0x00010177

[    6.729046] scsi 1:0:0:0: Direct-Access     ATA      WDC WD307AA      05.0 PQ: 0 ANSI: 5

[    6.729499] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]

[    6.729525] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18

[    6.729543] PCI: Setting latency timer of device 0000:00:1f.2 to 64

[    6.729584] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e502 bmdma 0x0001e800 irq 18

[    6.729617] ata4: SATA max UDMA/133 cmd 0x0001e600 ctl 0x0001e702 bmdma 0x0001e808 irq 18

[    6.729628] scsi3 : ata_piix

[    6.897311] ATA: abnormal status 0x7F on port 0x0001e407

[    6.897326] scsi4 : ata_piix

[    7.061712] ATA: abnormal status 0x7F on port 0x0001e607

[    7.069291] SCSI device sda: 60074784 512-byte hdwr sectors (30758 MB)

[    7.069313] sda: Write Protect is off

[    7.069318] sda: Mode Sense: 00 3a 00 00

[    7.069352] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    7.069430] SCSI device sda: 60074784 512-byte hdwr sectors (30758 MB)

[    7.069447] sda: Write Protect is off

[    7.069452] sda: Mode Sense: 00 3a 00 00

[    7.069481] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    7.069486]  sda: sda1 sda2 < sda5 >

[    7.104071] sd 1:0:0:0: Attached scsi disk sda

[    7.108471] sd 1:0:0:0: Attached scsi generic sg0 type 0

[    7.309361] Attempting manual resume

[    7.309365] swsusp: Resume From Partition 8:5

[    7.309367] PM: Checking swsusp image.

[    7.309640] PM: Resume from disk failed.

[    7.345911] kjournald starting.  Commit interval 5 seconds

[    7.345919] EXT3-fs: mounted filesystem with ordered data mode.

[   10.148237] usb-storage: device scan complete

[   10.148732] scsi 0:0:0:0: Direct-Access     Memorex  TD Classic 003C  5.00 PQ: 0 ANSI: 0 CCS

[   10.149958] SCSI device sdb: 1007616 512-byte hdwr sectors (516 MB)

[   10.150580] sdb: Write Protect is off

[   10.150584] sdb: Mode Sense: 23 00 00 00

[   10.150586] sdb: assuming drive cache: write through

[   10.152704] SCSI device sdb: 1007616 512-byte hdwr sectors (516 MB)

[   10.153327] sdb: Write Protect is off

[   10.153330] sdb: Mode Sense: 23 00 00 00

[   10.153332] sdb: assuming drive cache: write through

[   10.153335]  sdb: sdb1

[   10.154015] sd 0:0:0:0: Attached scsi removable disk sdb

[   10.154053] sd 0:0:0:0: Attached scsi generic sg1 type 0

[   23.712053] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   23.766249] input: PC Speaker as /class/input/input3

[   24.034497] parport: PnPBIOS parport detected.

[   24.034553] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

[   24.072191] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   24.100714] ieee80211_crypt: registered algorithm 'NULL'

[   24.123225] ieee80211: 802.11 data/management/control stack, git-1.1.13

[   24.123231] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

[   24.152363] iTCO_vendor_support: vendor-support=0

[   24.154927] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)

[   24.155102] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)

[   24.155156] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[   24.169258] parport0: Printer, HEWLETT-PACKARD DESKJET 720C

[   24.374417] intel_rng: FWH not detected

[   24.482040] bcm43xx driver

[   24.482150] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 21

[   24.551388] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   24.692704] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   24.696196] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   24.769751] Linux agpgart interface v0.102 (c) Dave Jones

[   24.825884] nvidia: module license 'NVIDIA' taints kernel.

[   24.899580] p54: LM86 firmware

[   25.079736] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

[   25.079749] PCI: Setting latency timer of device 0000:01:00.0 to 64

[   25.079934] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006

[   25.220415] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16

[   25.220437] PCI: Setting latency timer of device 0000:00:1b.0 to 64

[   25.743960] NET: Registered protocol family 17

[   25.897990] prism54usb: probe of 5-6:1.0 failed with error -110

[   25.898004] usbcore: registered new interface driver prism54usb

[   26.000122] fuse init (API version 7.8)

[   26.016992] lp0: using parport0 (interrupt-driven).

[   26.067240] Adding 1277128k swap on /dev/disk/by-uuid/a26ba0be-f655-41f9-b2cb-260ff895e371.  Priority:-1 extents:1 across:1277128k

[   26.242442] EXT3 FS on sda1, internal journal

[   31.647555] input: Power Button (FF) as /class/input/input4

[   31.647593] ACPI: Power Button (FF) [PWRF]

[   31.647644] input: Power Button (CM) as /class/input/input5

[   31.647681] ACPI: Power Button (CM) [PWRB]

[   31.769828] No dock devices found.

[   31.792485] Using specific hotkey driver

[   31.874921] ibm_acpi: ec object not found

[   31.954576] pcc_acpi: loading...

[   33.529756] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   36.634894] ppdev: user-space parallel port driver

[   37.376211] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   37.893261] apm: BIOS not found.

[   38.079983] Bluetooth: Core ver 2.11

[   38.080210] NET: Registered protocol family 31

[   38.080215] Bluetooth: HCI device and connection manager initialized

[   38.080221] Bluetooth: HCI socket layer initialized

[   38.095201] Bluetooth: L2CAP ver 2.8

[   38.095207] Bluetooth: L2CAP socket layer initialized

[   38.235064] Bluetooth: RFCOMM socket layer initialized

[   38.235506] Bluetooth: RFCOMM TTY layer initialized

[   38.235512] Bluetooth: RFCOMM ver 1.8

[   47.938647] NET: Registered protocol family 10

[   47.938769] lo: Disabled Privacy Extensions

[   58.329905] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

[   60.902852] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

---

### Post by VietxHieu on 2007-10-27
hmm did i code the right thing?

---

