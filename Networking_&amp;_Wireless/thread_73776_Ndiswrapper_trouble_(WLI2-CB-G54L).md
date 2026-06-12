---
title: "Ndiswrapper trouble (WLI2-CB-G54L)"
date: 2005-10-10
forum: Networking &amp; Wireless
---

### Post by kaamos on 2005-10-10
Hello!

I compiled ndiswrapper 1.4 from source and I'm trying to get my pcmcia wlan-card to work. The card is buffalo WLI2-CB-G54L and I'm using the driver mentioned in ndiswrapper wiki. I'm now able to see my wireless network but pinging to router doesn't work.

```

$ ndiswrapper -l
Installed ndis drivers:
neti2220                driver present, hardware present

$ iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:xx:xx:xx
                    ESSID:"perkele"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Everything looks good to me except the signal strength. Running iwconfig gives:

```

~$ iwconfig

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

The accesspoint isn't being recognised for some reason. The essid of the accesspoint is visible in network-admin and is set in /etc/network/interfaces. Iwconfig still gives ESSID:off/any and trying to set the essid again by "sudo iwconfig wlan0 essid perkele" gives no errors, but the output of iwconfig still doesn't change. Trying to set the accesspoint mac by hand gives:

```

$ sudo iwconfig wlan0 ap 00:90:4B:xx:xx:xx
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Invalid argument.
$ sudo iwconfig wlan0 ap 00:90:4B:xx:xx:xx
$

```

Strange. So sometimes it works and sometimes not? If the output gives the error, then an error message is visible in dmesg | tail. Either way, the output of iwconfig still remains the same. Trying to bring up wlan0 eventually timeouts:
```

$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:0b:42:b5:88
Sending on   LPF/wlan0/00:0d:0b:42:b5:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18

```
And so on..

The router has all security measures (wep & mac-address association) disabled so I really can't see why this doesn't work.

At this point ANY suggestions are welcome. :)

(BTW thank you for this great forum!)

---

### Post by kaamos on 2005-10-11
The plot thickens. It seems my ethernet-card is causing PCI interrupts with the wifi-card. Or if anyone has better ideas what these logs could mean, please let me know.

```

$ cat /var/log/messages | grep -i "irq 17"

Oct  9 22:42:49 localhost kernel: ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
Oct  9 22:42:49 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
Oct  9 22:42:49 localhost kernel: ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 22:42:49 localhost kernel: Yenta: ISA IRQ mask 0x0438, PCI irq 17
Oct  9 22:42:49 localhost kernel: ACPI: PCI interrupt 0000:02:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 22:42:49 localhost kernel: natsemi eth0: NatSemi DP8381[56] at 0xffdfe000 (0000:02:0c.0), 00:a0:cc:d7:ef:fe, IRQ 17, port TP.
Oct  9 22:42:49 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 22:42:49 localhost kernel: ndiswrapper: using irq 17
Oct  9 23:05:28 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 23:05:28 localhost kernel: ndiswrapper: using irq 17
Oct  9 23:20:16 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 23:20:16 localhost kernel: ndiswrapper: using irq 17
Oct  9 23:39:14 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  9 23:39:14 localhost kernel: ndiswrapper: using irq 17
.
.
.

```

And dmesg:

```

$ dmesg | grep -i "irq 17"

Yenta: ISA IRQ mask 0x0010, PCI irq 17
natsemi eth0: NatSemi DP8381[56] at 0xffdfe000 (0000:02:0c.0), 00:a0:cc:d7:ef:fe, IRQ 17, port TP.
ndiswrapper: using irq 17

```

Again, ALL ideas are more than welcome.

---

