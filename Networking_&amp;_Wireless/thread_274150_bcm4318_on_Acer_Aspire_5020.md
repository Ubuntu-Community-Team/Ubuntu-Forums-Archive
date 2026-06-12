---
title: "bcm4318 on Acer Aspire 5020"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by joff13 on 2006-10-09
Hi everyone,

I just got an Acer Aspire 5023 and installed ubuntu dapper 64 amd
```
~$ uname -r
2.6.15-27-amd64-generic
```

after lots of hours and guide and forums I decided to post here.

I tried using ndiswrapper as well as bcm43xx-fwcutter and it sems that both are working in fact:

```
$iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Cataratta"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```
and ```
 $ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F4:FC:28
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fef4:fc28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3622423 (3.4 MiB)  TX bytes:586199 (572.4 KiB)
          Interrupt:66 Base address:0x400

eth1      Link encap:Ethernet  HWaddr 00:16:CE:12:25:BE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:5208 (5.0 KiB)
          Interrupt:10 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
```

but no way to have the wlan working!
I think the problem is the hot key to activate the bcm card that does not work in fact:
```

$ tail /var/log/syslog
Oct  9 18:30:20 localhost kernel: [ 1337.895530] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
Oct  9 18:30:20 localhost kernel: [ 1337.895535] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
Oct  9 18:30:20 localhost kernel: [ 1337.974020] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
Oct  9 18:30:20 localhost kernel: [ 1337.974025] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
Oct  9 18:30:21 localhost kernel: [ 1338.502791] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
Oct  9 18:30:21 localhost kernel: [ 1338.502795] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
Oct  9 18:30:21 localhost kernel: [ 1338.547777] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
Oct  9 18:30:21 localhost kernel: [ 1338.547782] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
Oct  9 18:30:22 localhost kernel: [ 1338.937918] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
Oct  9 18:30:22 localhost kernel: [ 1338.937923] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.

```

I post this as well:
```
$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:16:ce:12:25:be
Sending on   LPF/eth1/00:16:ce:12:25:be
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I tried to compile acer_pci, but to many errors during the process.

Anyone have an idea about that?

tnx a lot to ereryone

Solution found!

insalling acer_apci the wlan works with ndiswrapper.

compiling problem solved

bye

---

### Post by finite9 on 2006-10-13
I have an Aspire 5021 working just fine with bcm43xx and acer_acpi 0.3.

By the way, do you use standard network scripts or Gnome network manager?  I would very much like to get this working 'automatically' with a GUI instead of the custom scripts that I had to make to get it to work.

---

### Post by joff13 on 2006-10-13
I solved the problem using ndiswrapper, driver downloaded from acer and using  acer_apci.

but I discovered that if i'm to far from the access point is difficult to acced. But for me to far is just upstairs... :-? 

btw i prefer the shell, the GUI give you no message to understand why something doesn't work

anyway thanks

---

