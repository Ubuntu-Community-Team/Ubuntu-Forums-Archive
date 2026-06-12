---
title: "Loses wireless internet connection"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by jlar on 2008-01-04
Hi,

I am experiencing problems with my wireless connection. After some time I lose my internet connection. When I plug in a cable between my computer and router this does not happen. Since my ISP does not offer a wireless router I have connected my wireless router to the ISP provided router with a cable (the ISP provided router has an additional plug for my telephone).

I am using Ubuntu 7.10, the wireless card is a D-Link Wireless N USB Adapter while the wireless router is a D-Link Wireless N Home Router.

Does anyone know what is wrong?

Here is the (tail of the) output from dmesg after it has failed:

```
[   39.077985] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[   39.229437] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[   39.402310] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,03/13/2007, 1.00.01.0000) loaded
[   39.737296] wlan0: ethernet device 00:1b:11:1b:87:42 using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 07D1:3C09.F.conf
[   39.737959] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   39.737987] usbcore: registered new interface driver ndiswrapper
[   39.786901] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   40.122384] EXT3 FS on sda1, internal journal
[   41.362185] No dock devices found.
[   41.471835] input: Power Button (FF) as /class/input/input4
[   41.475273] ACPI: Power Button (FF) [PWRF]
[   41.503139] input: Power Button (CM) as /class/input/input5
[   41.506551] ACPI: Power Button (CM) [PWRB]
[   43.149994] eth0: link down
[   44.124716] [drm] Initialized drm 1.1.0 20060810
[   44.135292] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   44.137276] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   44.585629] ppdev: user-space parallel port driver
[   45.292515] audit(1199424500.126:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4961 profile="/usr/sbin/cupsd"
[   45.488267] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.488271] apm: overridden by ACPI.
[   47.359878] Bluetooth: Core ver 2.11
[   47.359979] NET: Registered protocol family 31
[   47.359981] Bluetooth: HCI device and connection manager initialized
[   47.359984] Bluetooth: HCI socket layer initialized
[   47.381078] Bluetooth: L2CAP ver 2.8
[   47.381082] Bluetooth: L2CAP socket layer initialized
[   47.664593] Bluetooth: RFCOMM socket layer initialized
[   47.664756] Bluetooth: RFCOMM TTY layer initialized
[   47.664758] Bluetooth: RFCOMM ver 1.8
[   47.731706] Failure registering capabilities with primary security module.
[   75.752323] NET: Registered protocol family 17
[   92.145077] NET: Registered protocol family 10
[   92.145482] lo: Disabled Privacy Extensions
[   92.145758] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  102.577044] wlan0: no IPv6 routers present
```

And from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"eskemose"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1C:F0:58:28:E1   
          Bit Rate=130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And from ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1C:25:05:D5:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:1B:87:42  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fe1b:8742/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:946 (946.0 b)  TX bytes:7217 (7.0 KB)
```

---

### Post by Hightide on 2008-01-04
Hi

try Kevdogs tread. I found it very useful

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

regards

---

### Post by Paris Heng on 2008-01-06
Dear,

I see that your network configuration is correct. Since you using [COLOR="Red"]802.11n (N) [/COLOR]type Wifi card, did you check the compatibility of the NDISwrapper' version to the card itself?

---

