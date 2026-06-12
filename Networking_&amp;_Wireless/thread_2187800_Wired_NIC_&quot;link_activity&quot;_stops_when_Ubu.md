---
title: "Wired NIC &quot;link activity&quot; stops when Ubuntu starts"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by tsx_5 on 2013-11-13
Ok short description:

Turn on computer and watch the lights blink (green and yellow) on the NIC & network cable (cable connection looks like it's glowing), watch the TV screen as Ubuntu screen appears and watch as the lights on the NIC go black -- as well as the glowing lights from the network cable stop.  System fully starts and I have no wired network.  It shows cable as being disconnected.  BTW: this is on a fresh install of 12.04.

_Here comes the hardware info:_

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)


_What I have tried:_

1. powering everything down, pulling the plug, waiting a few minutes, plugging back in rebooting -- no dice
2. building the driver from Realtek (a major pain getting all the build stuff on the machine) -- no dice
3. turn off WIFI
4. check cable (smart TV is what I use as the display for this machine, network works fine with the TV and not with the box)
5. ifup


_And now some logs_

dmesg | grep r8169
[    1.592936] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.593261] r8169 0000:01:00.0: irq 45 for MSI/MSI-X
[    1.594103] r8169 0000:01:00.0 eth0: RTL8168evl/8111evl at 0xf840e000, 00:01:2e:4d:2a:8a, XID 0c900800 IRQ 45
[    1.594115] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    4.280613] r8169 0000:01:00.0 eth0: link down
[    4.280811] r8169 0000:01:00.0 eth0: link down
[ 1379.907440] r8169 0000:01:00.0 eth0: link down
[ 1379.907487] r8169 0000:01:00.0 eth0: link down

_ifconfig_ 
eth0      Link encap:Ethernet  HWaddr 00:01:2e:4d:2a:8a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:90800 (90.8 KB)  TX bytes:90800 (90.8 KB)

wlan0     Link encap:Ethernet  HWaddr 68:17:29:5a:53:66
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

_cat syslog | grep -e r8169 -e etwork_
Nov 13 19:13:44 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Nov 13 19:13:44 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 13 19:13:44 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): taking down device.
Nov 13 19:13:44 zbox-ZBOX-ID84 NetworkManager[797]: <info> WiFi hardware radio set disabled
Nov 13 19:13:44 zbox-ZBOX-ID84 NetworkManager[797]: <info> WiFi now disabled by radio killswitch
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> disable requested (sleeping: no  enabled: yes)
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> sleeping or disabling...
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): now unmanaged
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): cleaning up...
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): taking down device.
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): now unmanaged
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Nov 13 19:14:04 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): cleaning up...
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> enable requested (sleeping: no  enabled: no)
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> waking up and re-enabling...
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> WWAN now enabled by management service
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): now managed
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): bringing up device.
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): preparing device.
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (eth0): deactivating device (reason 'managed') [2]
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): now managed
Nov 13 19:14:12 zbox-ZBOX-ID84 kernel: [ 1379.907440] r8169 0000:01:00.0 eth0: link down
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 13 19:14:12 zbox-ZBOX-ID84 kernel: [ 1379.907487] r8169 0000:01:00.0 eth0: link down
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): bringing up device.
Nov 13 19:14:12 zbox-ZBOX-ID84 NetworkManager[797]: <info> (wlan0): deactivating device (reason 'managed') [2]

_nm-tool_
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        68:17:29:5A:53:66

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:01:2E:4D:2A:8A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

Suggestions Please   ](*,)

---

### Post by tsx_5 on 2013-11-14
Figured it out...

I had the wrong driver from reltek.  Once I got the right one all is working correctly.

---

