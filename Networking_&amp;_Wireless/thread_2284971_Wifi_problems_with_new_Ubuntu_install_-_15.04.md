---
title: "Wifi problems with new Ubuntu install - 15.04"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by alistair10 on 2015-07-02
I recently upgraded from Windows 8 to Linux Ubuntu 15.04 just a few days ago. But, when I sign in, the Wi-Fi connection is really slow to connect if not at all. The connection bar also states that I am always on 1-2 bars. Can anyone help with this? I've tried
```

sudo gedit /etc/nssswitch.conf

```
and changing:
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns

```
from default to:
```

hosts:          files dns

```
to no avail. Here's what happens after with lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f8:0f:41:65:35:f7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.15-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:f7c00000-f7c1ffff memory:f7c39000-f7c39fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 24:05:0f:34:32:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.19.0-21-generic firmware=0.29 ip=192.168.2.12 link=yes multicast=yes wireless=IEEE 802.11abgn

```

If any more detail is needed, I'd be happy to post it here.

---

### Post by alistair10 on 2015-07-03
Might also want to note - my network can support IPv6.
Here's from iwconfig:
```

eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"belkin.9c9"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:56:59:C9   
          Bit Rate=115.6 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7509  Invalid misc:26   Missed beacon:0


lo        no wireless extensions.



```

And ifconfig:

```

eth0      Link encap:Ethernet  HWaddr f8:0f:41:65:35:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:535430 (535.4 KB)  TX bytes:535430 (535.4 KB)


wlan0     Link encap:Ethernet  HWaddr 24:05:0f:34:32:b5  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2605:fff:fe34:32b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:755825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:479969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:971163982 (971.1 MB)  TX bytes:49050959 (49.0 MB)

```

I found out my driver is "rt2800usb" also. Not quite sure what that means. I just want a solution to this.

---

