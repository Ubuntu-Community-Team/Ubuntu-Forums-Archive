---
title: "wifi won't reconnect after connection is lost (rtl8180)"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Syzothermy on 2008-11-15
My Gateway MX3414 laptop (wifi card: rtl8180) (running: ubuntu 8.10) will connect to a wireless point (wep encrypted) just fine on startup, however, if the connection is ever lost, it won't reconnect. Kind of annoying, since I have to reboot every time it disconnects, and I can't leave stuff that needs the internet running (Like, for example, torrents) overnight and expect it to work the next morning.

following [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) ...



```
**$ lspci**
[...]
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

```
**$ ifconfig**
[...]
wlan0 Link encap:Ethernet HWaddr 00:c0:a8:bc:d3:90
          inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:febc:d390/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:2419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1813324 (1.8 MB) TX bytes:472628 (472.6 KB)
```

```
**$ ifconfig**
[...]
wlan0 IEEE 802.11bg ESSID:"S-Net"
          Mode:Managed Frequency:2.412 GHz Access Point: 00:18:01:FA:80:21
          Bit Rate=36 Mb/s Tx-Power=27 dBm
          Retry min limit:7 RTS thr:off Fragment thr=2352 B
          Power Management:off
          Link Quality=16/100 Signal level:39/65
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

```
**$ dmesg | grep "wlan0"**
[ 82.392076] wlan0: authenticate with AP 00:18:01:fa:80:21
[ 82.393627] wlan0: authenticated
[ 82.393636] wlan0: associate with AP 00:18:01:fa:80:21
[ 82.397050] wlan0: RX AssocResp from 00:18:01:fa:80:21 (capab=0x431 status=0 aid=1)
[ 82.397064] wlan0: associated
[ 119.480044] wlan0: no IPv6 routers present
```

```
**$ sudo lshw -C network**
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:bc:d3:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.5 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:cb:dd:52:01:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
**$ iwlist scan**
[...]
wlan0 Scan completed :
          Cell 01 - Address: 00:18:01:FA:80:21
                    ESSID:"S-Net"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=8/100 Signal level:40/65
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000302ca2c9181
                    Extra: Last beacon: 80ms ago
```

```
**$ lsb_release -d**
Description: Ubuntu 8.10
```

```
**$ uname -mr**
2.6.27-7-generic i686
```

```
**$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces... Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```

---

