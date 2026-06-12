---
title: "Inspiron 5160 - wireless not working"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by negus777 on 2006-09-20
I was able to get the wireless adapter to work on "warty warthog" but am having no success on the versions since then. I am currently up to "Dapper Drake"

I am hoping from the information I am including someone can spot my problem and point it out, does anyone successfully use wireless with the Dell Inspiron 5160 Broadcom chipset?

rasnegus@negus777:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.





rasnegus@negus777:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:51:6F:58
                    ESSID:"Intersol"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.


Portion of dmesg
-----------------
[17179596.340000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.388000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179596.516000] ndiswrapper: driver bcmwl5 (Broadcom,06/25/2004, 3.40.73.0) loaded
[17179596.516000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179596.524000] ndiswrapper: using irq 193
[17179596.648000] NET: Registered protocol family 17
[17179597.648000] wlan0: vendor: ''
[17179597.648000] wlan0: ndiswrapper ethernet device 00:0b:7d:08:d9:4d using driver bcmwl5, 14E4:4320.5.conf
[17179597.648000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA

Another portion of dmesg
------------------------
[17179605.972000] pcc_acpi: loading...
[17179606.064000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179606.592000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179607.424000] b44: eth0: Link is down.
[17179610.424000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179610.424000] b44: eth0: Flow control is off for TX and off for RX.
[17179612.656000] NET: Registered protocol family 10
[17179612.656000] lo: Disabled Privacy Extensions
[17179612.656000] IPv6 over IPv4 tunneling driver
[17179612.944000] ppdev: user-space parallel port driver
[17179613.512000] apm: BIOS not found.
[17179617.220000] ip_tables: (C) 2000-2002 Netfilter core team
[17179617.356000] Netfilter messages via NETLINK v0.30.
[17179617.376000] ip_conntrack version 2.4 (8190 buckets, 65520 max) - 232 bytes per conntrack
[17179619.276000] Bluetooth: Core ver 2.8
[17179619.276000] NET: Registered protocol family 31
[17179619.276000] Bluetooth: HCI device and connection manager initialized
[17179619.276000] Bluetooth: HCI socket layer initialized
[17179619.316000] Bluetooth: L2CAP ver 2.8
[17179619.316000] Bluetooth: L2CAP socket layer initialized
[17179619.320000] Bluetooth: RFCOMM socket layer initialized
[17179619.320000] Bluetooth: RFCOMM TTY layer initialized
[17179619.320000] Bluetooth: RFCOMM ver 1.7
[17179622.784000] eth0: no IPv6 routers present
[17179623.140000] wlan0: no IPv6 routers present


rasnegus@negus777:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
bcmwl5          driver present, hardware present




rasnegus@negus777:~$ vi /etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:1f:27:a9:e1 arp 1
wlan0 mac 00:0b:7d:08:d9:4d arp 1

---

### Post by happy-and-lost on 2006-09-23
Right. Your radio is off.

Go into your laptop's BIOS and have a look around. There should be one or two wireless card setting in there. One of them will be something like "Card always on/not Fn-F2" (can't remember, it will be fairly obvious). If not obvious. Play around, you might get somewhere!

---

