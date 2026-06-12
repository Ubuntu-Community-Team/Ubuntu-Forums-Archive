---
title: "Wifi sees AP, but will not connect."
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by mike310z on 2008-09-06
I just did a brand new install of 8.04 via a wired lan, it pulled all the latest updates, it pulled restricted drivers for ATI and 43b.
I see the little icon, it shows my SSID and signal strength, I turned off all encryption, I turned it on, I changed channels.
I tried setting it basically using every permutation and suggestion without any luck.

When booted via windows, its perfect.

Attached are dumps I made after my last abortive attempt to get connected, I infer from them that the driver is there
> BCM4306 802.11b/g Wireless LAN Controller
configuration: driver=b43-pci-bridge latency=64 module=ssb 
and does see the AP,
> wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:76:53:E8
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level=-45 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000011beed118e 

but it just will not  connect.

I see lots of similar threads, but I am failing only at the last step. Thoughts appreciated.

Mike

```

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:76:53:E8   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:76:53:E8
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level=-45 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000011beed118e

  *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:b4:5a:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:64:c8:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by mike310z on 2008-09-06
This is the result of a manual configuration from the shell.

> mike@desktop:~$ sudo ifconfig wlan0 down
mike@desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:64:c8:28
Sending on   LPF/wlan0/00:0c:41:64:c8:28
Sending on   Socket/fallback
mike@desktop:~$ sudo ifconfig wlan0 up
mike@desktop:~$ sudo iwconfig wlan0 essid "linksys"
mike@desktop:~$ sudo iwconfig wlan0 mode Managed
mike@desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:64:c8:28
Sending on   LPF/wlan0/00:0c:41:64:c8:28
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by morris8809 on 2008-09-06
im having the same exact problem with 8.04 ubuntu ultimate edition 1.9. I can see all kinds of access points, i can connect to unencrypted but when wep or wpa is enabled it will not pull an ip address. ????:confused:

---

### Post by girishsasikumar on 2008-09-06
Since U r able to connect to unencrypted networks, the problem must be in the encryption type that u r choosing, there are atleast 8 different encryption types 'WEP 64/128 bit HEX','128 bit pass phrase', etc. Did u try them out with yuor network manager ??? I think that should solve the problem

---

### Post by mike310z on 2008-09-06
I can see the access points, but can not connect with or without encryption, I have tried just about every combination.

DMESG says
> [   38.043848] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[   38.059273] b43-phy0: Broadcom 4306 WLAN found
[   38.059394] usbcore: registered new interface driver uvcvideo
[   38.059401] USB Video Class driver (v0.1.0)
[   38.083026] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   38.083051] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   38.107865] phy0: Selected rate control algorithm 'simple'
[   38.426828] intel8x0_measure_ac97_clock: measured 56242 usecs
[   38.426837] intel8x0: clocking to 48000
[   39.520819] lp0: using parport0 (interrupt-driven).
[   39.584604] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   40.146197] EXT3 FS on sda1, internal journal
[   41.641969] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.061632] No dock devices found.
[   43.382311] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.382319] apm: disabled - APM is not SMP safe.
[   43.641539] ppdev: user-space parallel port driver
[   43.763349] audit(1220720529.333:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5087 profile="/usr/sbin/cupsd" namespace="default"
[   45.156002] input: b43-phy0 as /devices/virtual/input/input6
[   45.189121] Bluetooth: Core ver 2.11
[   45.189546] NET: Registered protocol family 31
[   45.189551] Bluetooth: HCI device and connection manager initialized
[   45.189557] Bluetooth: HCI socket layer initialized
[   45.244408] Bluetooth: L2CAP ver 2.9
[   45.244414] Bluetooth: L2CAP socket layer initialized
[   45.349102] Bluetooth: RFCOMM socket layer initialized
[   45.349128] Bluetooth: RFCOMM TTY layer initialized
[   45.349131] Bluetooth: RFCOMM ver 1.8
[   45.645925] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   46.889412] b43-phy0 debug: Chip initialized
[   46.889666] b43-phy0 debug: 30-bit DMA initialized
[   46.890049] Registered led device: b43-phy0:tx
[   46.890261] Registered led device: b43-phy0:rx
[   46.890468] Registered led device: b43-phy0:radio
[   46.890499] b43-phy0 debug: Wireless interface started
[   46.938118] b43-phy0 debug: Adding Interface type 2
[   47.685521] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.186234] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   50.186243] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   50.186249] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   50.186397] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   50.186416] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   50.186454] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   50.186482] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   50.192312] [fglrx] GART Table is not in FRAME_BUFFER range 
[   50.192325] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   50.192331] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[   50.294424] [fglrx] interrupt source 20008000 successfully enabled
[   50.294434] [fglrx] enable ID = 0x00000004
[   50.294447] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   50.294622] [fglrx] interrupt source 10000000 successfully enabled
[   50.294625] [fglrx] enable ID = 0x00000005
[   50.294632] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   68.754179] NET: Registered protocol family 10
[   68.754720] lo: Disabled Privacy Extensions
[   68.755517] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.756527] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  572.509981] wlan0: Initial auth_alg=0
[  572.509993] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  572.705863] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  572.905745] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  573.106630] wlan0: authentication with AP 00:0c:41:76:53:e8 timed out
[  574.517802] b43-phy0 debug: Removing Interface type 2
[  574.585975] b43-phy0 debug: Wireless interface stopped
[  574.586208] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[  574.586313] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  574.593770] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  574.601768] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  574.609754] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  574.617754] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 128/128
[  574.624791] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  574.663078] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  574.689265] input: b43-phy0 as /devices/virtual/input/input7
[  574.851481] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  576.084168] b43-phy0 debug: Chip initialized
[  576.084456] b43-phy0 debug: 30-bit DMA initialized
[  576.085046] Registered led device: b43-phy0:tx
[  576.085252] Registered led device: b43-phy0:rx
[  576.085458] Registered led device: b43-phy0:radio
[  576.085490] b43-phy0 debug: Wireless interface started
[  576.136129] b43-phy0 debug: Adding Interface type 2
[  576.142631] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  576.218034] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  578.244926] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  630.257506] NET: Registered protocol family 17
[  837.127479] b43-phy0 debug: Removing Interface type 2
[  837.199528] b43-phy0 debug: Wireless interface stopped
[  837.199723] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[  837.199791] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  837.207454] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  837.215576] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  837.223444] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  837.231434] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 44/128
[  837.239456] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  837.380591] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  837.420030] input: b43-phy0 as /devices/virtual/input/input8
[  837.594344] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  838.834762] b43-phy0 debug: Chip initialized
[  838.835044] b43-phy0 debug: 30-bit DMA initialized
[  838.835431] Registered led device: b43-phy0:tx
[  838.835648] Registered led device: b43-phy0:rx
[  838.835855] Registered led device: b43-phy0:radio
[  838.835890] b43-phy0 debug: Wireless interface started
[  838.874740] b43-phy0 debug: Adding Interface type 2
[  838.881277] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  841.002212] b43-phy0 debug: Removing Interface type 2
[  841.078178] b43-phy0 debug: Wireless interface stopped
[  841.078374] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[  841.078451] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  841.086180] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  841.094160] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  841.102155] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  841.110151] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 22/128
[  841.118157] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  843.170172] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  843.197351] input: b43-phy0 as /devices/virtual/input/input9
[  843.362466] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  844.595399] b43-phy0 debug: Chip initialized
[  844.595681] b43-phy0 debug: 30-bit DMA initialized
[  844.597364] Registered led device: b43-phy0:tx
[  844.597708] Registered led device: b43-phy0:rx
[  844.598057] Registered led device: b43-phy0:radio
[  844.598098] b43-phy0 debug: Wireless interface started
[  844.635381] b43-phy0 debug: Adding Interface type 2
[  844.641928] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  881.458005] wlan0: Initial auth_alg=0
[  881.458017] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  881.657485] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  881.857363] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  882.057246] wlan0: authentication with AP 00:0c:41:76:53:e8 timed out

---

