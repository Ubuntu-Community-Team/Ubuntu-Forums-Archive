---
title: "wlan timeout"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by nathanhillinbl on 2007-03-24
I just switched to kde a week ago, and since i switched, if i dont keep a high stream of data going over the wlan, it times out, and i lose connection. I have no hard wired access, and its pissing me off to have to turn my computer off then back on when i want to use the internet. For example. i might not be able to sent this message the first time, because theres no data being sent. How do i fix this?

Any help would be greatly appreciated,
Nate Hill

---

### Post by nathanhillinbl on 2007-03-24
anyone, i've had to restart my computer 15 times today!!!!!

---

### Post by nathanhillinbl on 2007-03-28
i've been messing with this ever since i first posted, and its confusing, and a little discouraging that i have to restart my computer every 10 mins to use the internet. I ask anyone that knows anything that would be of help, please give any input that you can.


Thank You,
Nate Hill

---

### Post by chili555 on 2007-03-28
I hardly know a thing, but maybe we can get the group going. Please take a look at:```
sudo cat /var/log/messages | grep eth1
```Substitute your wireless interface here, ath0 or wlan0 or ...? This will tell us if the kernel is complaining, in any way, about the initialization or running of your interface. Also look in:```
dmesg | grep eth1
```

Is this an ndiswrapper install or native drivers? May we see:```
sudo iwconfig eth1
```Obscure any encrytion codes.

---

### Post by nathanhillinbl on 2007-03-28
```
Mar 22 19:04:56 nate-desktop kernel: [17179592.904000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 22 19:04:56 nate-desktop kernel: [17179592.904000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 22 19:04:56 nate-desktop kernel: [17179592.904000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 23 06:59:24 nate-desktop kernel: [17179592.984000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 23 06:59:24 nate-desktop kernel: [17179592.984000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 23 06:59:24 nate-desktop kernel: [17179592.984000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 23 15:37:01 nate-desktop kernel: [17179588.320000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 23 15:37:01 nate-desktop kernel: [17179588.320000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 23 15:37:01 nate-desktop kernel: [17179588.320000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 23 15:54:21 nate-desktop kernel: [17180638.528000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 15:59:39 nate-desktop kernel: [17179590.352000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 23 15:59:39 nate-desktop kernel: [17179590.352000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 23 15:59:39 nate-desktop kernel: [17179590.352000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 23 19:19:18 nate-desktop kernel: [17191574.948000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 19:19:26 nate-desktop kernel: [17191582.704000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 19:19:47 nate-desktop kernel: [17191604.120000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 19:21:18 nate-desktop kernel: [17179591.568000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 23 19:21:18 nate-desktop kernel: [17179591.568000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 23 19:21:18 nate-desktop kernel: [17179591.568000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 23 23:21:23 nate-desktop kernel: [17179590.484000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 23 23:21:23 nate-desktop kernel: [17179590.484000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 23 23:21:23 nate-desktop kernel: [17179590.484000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 08:59:46 nate-desktop kernel: [17179591.504000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 08:59:46 nate-desktop kernel: [17179591.504000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 08:59:46 nate-desktop kernel: [17179591.504000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 09:06:33 nate-desktop kernel: [17180009.072000] Inbound IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=234.21.81.1 LEN=226 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=17744 DPT=6347 LEN=206 
Mar 24 09:37:09 nate-desktop kernel: [17181845.016000] Inbound IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=234.21.81.1 LEN=212 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=17744 DPT=6347 LEN=192 
Mar 24 09:38:11 nate-desktop kernel: [17181906.604000] Inbound IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=234.21.81.1 LEN=214 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=17744 DPT=6347 LEN=194 
Mar 24 10:17:03 nate-desktop kernel: [17184238.424000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 10:17:15 nate-desktop kernel: [17184250.808000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 10:18:37 nate-desktop kernel: [17179592.112000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 10:18:37 nate-desktop kernel: [17179592.112000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 10:18:37 nate-desktop kernel: [17179592.112000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 10:25:25 nate-desktop kernel: [17179588.988000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 10:25:25 nate-desktop kernel: [17179588.988000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 10:25:25 nate-desktop kernel: [17179588.988000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 10:32:12 nate-desktop kernel: [17179592.516000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 10:32:12 nate-desktop kernel: [17179592.516000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 10:32:12 nate-desktop kernel: [17179592.516000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 11:40:45 nate-desktop kernel: [17183711.828000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 11:41:48 nate-desktop kernel: [17183775.084000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 11:42:48 nate-desktop kernel: [17183834.476000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 11:42:54 nate-desktop kernel: [17183840.480000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 13:36:30 nate-desktop kernel: [17179589.568000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 13:36:30 nate-desktop kernel: [17179589.568000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 13:36:30 nate-desktop kernel: [17179589.568000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 13:44:04 nate-desktop kernel: [17180051.152000] ndiswrapper: device wlan0 removed
Mar 24 13:45:23 nate-desktop kernel: [17179595.456000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 13:45:23 nate-desktop kernel: [17179595.456000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 13:45:23 nate-desktop kernel: [17179595.456000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 13:53:11 nate-desktop kernel: [17180070.984000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 24 14:10:53 nate-desktop kernel: [17179593.556000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 14:10:53 nate-desktop kernel: [17179593.556000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 14:10:53 nate-desktop kernel: [17179593.556000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 16:53:51 nate-desktop kernel: [17179589.456000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 16:53:51 nate-desktop kernel: [17179589.456000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 16:53:51 nate-desktop kernel: [17179589.456000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 20:11:05 nate-desktop kernel: [17179590.480000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 20:11:05 nate-desktop kernel: [17179590.480000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 20:11:05 nate-desktop kernel: [17179590.480000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 24 22:54:09 nate-desktop kernel: [17179590.580000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 24 22:54:09 nate-desktop kernel: [17179590.580000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 24 22:54:09 nate-desktop kernel: [17179590.580000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 26 06:35:10 nate-desktop kernel: [17179589.076000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 26 06:35:10 nate-desktop kernel: [17179589.076000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 26 06:35:10 nate-desktop kernel: [17179589.076000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 26 17:02:17 nate-desktop kernel: [17179589.904000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 26 17:02:17 nate-desktop kernel: [17179589.904000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 26 17:02:17 nate-desktop kernel: [17179589.904000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 15:14:55 nate-desktop kernel: [17179591.776000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 15:14:55 nate-desktop kernel: [17179591.776000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 15:14:55 nate-desktop kernel: [17179591.776000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 16:20:13 nate-desktop kernel: [17179590.036000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 16:20:13 nate-desktop kernel: [17179590.036000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 16:20:13 nate-desktop kernel: [17179590.036000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 16:23:34 nate-desktop kernel: [17179590.476000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 16:23:34 nate-desktop kernel: [17179590.476000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 16:23:34 nate-desktop kernel: [17179590.476000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 17:02:26 nate-desktop kernel: [17179589.396000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 17:02:26 nate-desktop kernel: [17179589.396000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 17:02:26 nate-desktop kernel: [17179589.396000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 17:20:47 nate-desktop kernel: [17179589.280000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 17:20:47 nate-desktop kernel: [17179589.280000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 17:20:47 nate-desktop kernel: [17179589.280000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 17:33:51 nate-desktop kernel: [17179589.728000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 17:33:51 nate-desktop kernel: [17179589.728000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 17:33:51 nate-desktop kernel: [17179589.728000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 17:43:22 nate-desktop kernel: [17179590.044000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 17:43:22 nate-desktop kernel: [17179590.044000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 17:43:22 nate-desktop kernel: [17179590.044000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 18:04:06 nate-desktop kernel: [17179592.676000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 18:04:06 nate-desktop kernel: [17179592.676000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 18:04:06 nate-desktop kernel: [17179592.676000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 18:04:18 nate-desktop kernel: [17179610.608000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 27 18:04:22 nate-desktop kernel: [17179614.384000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 27 18:44:19 nate-desktop kernel: [17179592.116000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 18:44:19 nate-desktop kernel: [17179592.116000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 18:44:19 nate-desktop kernel: [17179592.116000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 20:55:24 nate-desktop kernel: [17179588.452000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 20:55:24 nate-desktop kernel: [17179588.452000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 20:55:24 nate-desktop kernel: [17179588.452000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 21:19:03 nate-desktop kernel: [17179591.968000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 21:19:03 nate-desktop kernel: [17179591.968000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 21:19:03 nate-desktop kernel: [17179591.968000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 21:19:15 nate-desktop kernel: [17179609.900000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 27 21:19:34 nate-desktop kernel: [17179628.728000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 27 21:54:04 nate-desktop kernel: [17179591.684000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 27 21:54:04 nate-desktop kernel: [17179591.684000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 27 21:54:04 nate-desktop kernel: [17179591.684000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 27 21:54:15 nate-desktop kernel: [17179610.508000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 27 21:55:23 nate-desktop kernel: [17179677.668000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 28 15:15:41 nate-desktop kernel: [17179591.432000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 28 15:15:41 nate-desktop kernel: [17179591.432000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 28 15:15:41 nate-desktop kernel: [17179591.432000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 28 15:23:45 nate-desktop kernel: [17179588.204000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 28 15:23:45 nate-desktop kernel: [17179588.204000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 28 15:23:45 nate-desktop kernel: [17179588.204000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 28 15:54:50 nate-desktop kernel: [17179591.404000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
Mar 28 15:54:50 nate-desktop kernel: [17179591.404000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
Mar 28 15:54:50 nate-desktop kernel: [17179591.404000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
nate@nate-desktop:~$ 


```

That was the first command

```
nate@nate-desktop:~$ dmesg | grep wlan0
[17179591.404000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
[17179591.404000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
[17179591.404000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17179613.008000] wlan0: no IPv6 routers present
nate@nate-desktop:~$ 

```

That was the second

```
[17179613.008000] wlan0: no IPv6 routers present
nate@nate-desktop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:18:46:6D   
          Bit Rate:11 Mb/s   Tx-Power:17 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-84 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nate@nate-desktop:~$ 

```


The third one, and yes theres no encryption, its not my router, not my choice.

---

### Post by nathanhillinbl on 2007-03-28
from reading other posts, i'm not sure other people have had the same results as me, it seems to be a unique problem. Can anyone take the time to read what i've posted.

---

### Post by nathanhillinbl on 2007-03-28
i will also post a dmesg with something about my wlan card in it :

```
[17179588.032000] ndiswrapper: using irq 58
[17179588.404000] usbcore: registered new driver hiddev
[17179588.412000] input: Logitech Optical USB Mouse as /class/input/input2
[17179588.412000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-2
[17179588.412000] usbcore: registered new driver usbhid
[17179588.412000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.452000] ts: Compaq touchscreen protocol output
[17179588.784000] wlan0: vendor: 'Driver for INPROCOMM IPN2120 Wireless LAN Cards'
[17179588.784000] wlan0: ethernet device 00:12:17:d7:18:7f using NDIS driver lsipnds, 17FE:2120:1737:0020.5.conf
[17179588.784000] ndiswrapper (set_encr_mode:689): setting encryption mode to 0 failed (00010003)
[17179588.784000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17179588.792000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179588.792000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
[17179588.792000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179588.852000] NET: Registered protocol family 17
[17179589.112000] intel8x0_measure_ac97_clock: measured 54823 usecs
[17179589.112000] intel8x0: clocking to 46991
[17179589.112000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179589.112000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 66
[17179589.112000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179589.112000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179589.472000] lp0: using parport0 (interrupt-driven).
[17179589.512000] fuse init (API version 7.6)
[17179589.568000] Unable to find swap-space signature
[17179589.644000] EXT3 FS on hdc1, internal journal
[17179589.792000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179589.792000] md: bitmap version 4.39
[17179589.960000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179590.648000] Unable to find swap-space signature
[17179595.116000] ACPI: Power Button (FF) [PWRF]
[17179595.116000] ACPI: Power Button (CM) [PWRB]
[17179595.192000] ibm_acpi: ec object not found
[17179595.220000] pcc_acpi: loading...
[17179595.500000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179595.500000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa (1300 mV)
[17179595.500000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc (1250 mV)
[17179595.500000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe (1200 mV)
[17179595.500000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179595.500000] cpu_init done, current fid 0xe, vid 0xa
[17179599.968000] NET: Registered protocol family 10
[17179599.968000] lo: Disabled Privacy Extensions
[17179599.968000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179599.968000] IPv6 over IPv4 tunneling driver
[17179600.876000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179600.876000] apm: overridden by ACPI.
[17179608.968000] Bluetooth: Core ver 2.8
[17179608.968000] NET: Registered protocol family 31
[17179608.968000] Bluetooth: HCI device and connection manager initialized
[17179608.968000] Bluetooth: HCI socket layer initialized
[17179609.032000] Bluetooth: L2CAP ver 2.8
[17179609.032000] Bluetooth: L2CAP socket layer initialized
[17179609.036000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179609.076000] Bluetooth: RFCOMM socket layer initialized
[17179609.076000] Bluetooth: RFCOMM TTY layer initialized
[17179609.076000] Bluetooth: RFCOMM ver 1.7
[17179610.352000] wlan0: no IPv6 routers present
nate@nate-desktop:~$ 

```

---

### Post by nathanhillinbl on 2007-03-31
i have been messing with the router, reading tutorials, and have still got nowhere, i would like to again ask anyone who has any input to please let me know by posting. Thanks,
                                                                                                                                      Nate

---

