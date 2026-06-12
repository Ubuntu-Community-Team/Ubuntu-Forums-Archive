---
title: "My atheros based card stops working every 5th minute"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by chris-t on 2007-07-26
I know there's a lot of post about Atheros cards, but believe me i've searched with no succes.  

Anyway my problem is that i finally got my atheros card up and running with madwifi but it wont stay up. If i read the same page for like 5 minutes it just jumps off, and i have to disable and then enable it again (whith the gui tool, ifconfig set ath0 down doesn't do the trick.

I don't if it helps you but ifconfig gives me this:

ath0      Link encap:Ethernet  HWaddr 00:15:AF:24:B4:A9
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe24:b4a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3656583 (3.4 MiB)  TX bytes:607180 (592.9 KiB)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:60:FC:2D
          inet6 addr: fe80::216:d4ff:fe60:fc2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:10386 (10.1 KiB)
          Interrupt:185 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3926 (3.8 KiB)  TX bytes:3926 (3.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-24-B4-A9-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12216 errors:0 dropped:0 overruns:0 frame:3
          TX packets:3315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:4369809 (4.1 MiB)  TX bytes:681382 (665.4 KiB)
          Interrupt:169

cheers

---

### Post by srt4play on 2007-07-26
Hi chris-t.  What version of Ubuntu are you using?  I have an atheros based pci wlan card that would disconnect frequently in Edgy, but works much much better in Feisty.

---

### Post by chris-t on 2007-07-26
> **srt4play said:**
> Hi chris-t.  What version of Ubuntu are you using?  I have an atheros based pci wlan card that would disconnect frequently in Edgy, but works much much better in Feisty.

i'm using feisty 386

---

### Post by ugm6hr on 2007-07-27
Are you using WPA?  If so - Network Manager and madwifi don't behave very well together (automatic disconnect / reconnect cycle).  Try Wicd instead: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

