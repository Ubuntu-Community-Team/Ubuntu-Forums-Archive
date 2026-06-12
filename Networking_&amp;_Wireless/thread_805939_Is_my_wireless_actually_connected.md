---
title: "Is my wireless actually connected?"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Atra_Phasma on 2008-05-24
After recently getting my wireless card to work after disabling the r818x driver on the blacklist, i can connect to my network and get a message "Wireless Network Connection to "myessid" 30%", but i don't have an IP address. What can I do to fix this problem? I'm a bit of a newbie when it comes to Ubuntu, so any sugestions at all would be appreciated.
Thanks
Atra.

---

### Post by Atra_Phasma on 2008-05-24
bump*?

---

### Post by mapes12 on 2008-05-24
Please can you give us the output to

```
sudo lshw -C network
```

```
cat /etc/resolv.conf
```

```
ifconfig
```

```
iwconfig
```

```
iwlist scan
```

```
cat /etc/network/interfaces

```

Please post the output using quotes: 4th button in from the right.

---

### Post by Atra_Phasma on 2008-05-24
sure. sorry for the long response.... was mowing the lawn while i waited. just a second.

---

### Post by Atra_Phasma on 2008-05-24
```

sudo lshw -C network

```
yeilded this:
```

*-network
      description: Wireless Interface
      product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
      vendor: Realtek Semiconductor Co. , Ltd.
      physical id: 0
      bus info: pci@01:00.0
      logical name: wlan0
      version: 20
      serial: 00:13:f7:3b:22:41
      width:32bits
      clock: 33mhz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingt=32 multicast=yes wireless=802.11b/g linked
      resources: ioport:d800-d8ff iomemory:fbfffc00-fbfffdff irq:21

```
and
```

cat /etc/resolv.conf

```
yielded this:
```

nameserver 192.168.0.1

```
and this:
```

ifconfig

```
yielded this:
```

eth0       Link encap:Ethernet HWaddr 00:16:17:74:94
           UP BROADCAST MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0b) TX bytes:0 (0.0b)
           Interrupt:17 Base address:0x8000

eth1       Link encap:Ethernet HWaddr 00:16:17:74:8B:02
           UP BROADCAST MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0b) TX bytes:0 (0.0b)
           Interrupt:18    

lo         Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:144 errors:0 dropped:0 overruns:0 frame:0
           TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:9768 (9.5 KiB) TX bytes:9768 (9.5 KiB)

wlan0      Link encap:Ethernet HWaddr 00:13:F7:3B:22:41
           inet6 addr: fe80::213:f7ff:fe3b:2241/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:305 errors:1509 dropped:3459 overruns:0 frame:0    
           TX packets:4216 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:95749 (93.5 KiB)  TX bytes:214122 (209.1 KiB)
           Interrupt:21 Memory:f928ad00

```
This:
```

iwconfig

```
yielded this:
```

lo       no wireless extensions.

eth0     no wireless extensions.

wlan0    802.11b/g linked ESSID:"Dobill"
         Mode:Managed Frequency:2.462 GHz Access Point: 00:15:E9:71:01:AA
         Bit Rate=54 Mb/s
         Retry:on Fragment thr:of
         Power Management:off
         Link Quality:0 signal level:0 Noise levle:0
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```
and this:
```

iwlist scan

```
yielded this:
```

lo       Interface doesn't support scanning.

eth0     Interface doesn't support scanning.

eth1     Interface doesn't support scanning.

wlan0    Scan completed:
         Cell 01 - Address: 00:15:E9:71:01:AA
                   ESSID:"Dobill"
                   Protocol:IEEE 802.11bg
                   Mode:Master
                   Channel:11
                   Encryption key:on
                   Bit Rates:54 Mb/s
                   Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                   Quality:0 Signal level:0 Noise level:158
                   Extra: Last becon: 0ms ago

```
and finally, this:
```

cat /etc/network/interfaces

```
yielded this:
```

# This file describes the netowkr interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```
Hope this helps!

---

### Post by Atra_Phasma on 2008-05-25
actually, last night i believe i figured this out. I accidentally screwed up my wubi home.virtual.disk file, and had to reinstall, and all i did was disable the blacklisted r818x and r8187 drivers, and now it seems that i can set it up; i have established a successful connection to the internet twice. so i'm going to tentatively mark this as solved. but thank you for all of your help.

---

