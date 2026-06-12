---
title: "Wifi configuration ( problem with WPA )"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by peter07 on 2006-12-15
I'm trying to configure my wifi connection, but I have problem with WPA. I've tried Wifi-Radar. It has show my AP correctly, but I can't connect, becouse I must have WPA-active, but I don't know how I can turn it on using wifi-radar. I've also tried network-manager, but it hasn't detect anything. Please help

---

### Post by peter07 on 2006-12-15
Some more info:

My network manager:

[IMG]http://img279.imageshack.us/img279/8113/ubuntuvu2.png[/IMG]

My ( something like this, but I can't connect to the network):

[IMG]http://7thguard.net/files/przeglad_wifi/wifiradar_th.png[/IMG]

Please help

---

### Post by peter07 on 2006-12-16
Some more info:

my card:
```
Atheros Communication AR50056
```
I think my OS recognized it correctly, but I have problems with connection. First some more info, that may help you to help me ;)
```
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:E3:83:0D:04 
          inet6 addr: fe80::216:e3ff:fe83:d04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:36:8A:5B:B8 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x8000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11604 (11.3 KiB)  TX bytes:11604 (11.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-83-0D-04-00-00-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1390 errors:0 dropped:0 overruns:0 frame:17369
          TX packets:3234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:137026 (133.8 KiB)  TX bytes:154984 (151.3 KiB)
          Interrupt:193 Memory:dca00000-dca10000
```
And now iwconfig:
```
iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"siec"  Nickname:"siec"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:195  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions. 
```
It seams to look OK? 
What I have done to connect? First I installed two applications, that should help me: network-manager and wifi-radar. When I try to run first one, it doesn't recognize any AP. I've got only error message:
```
sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <information>   eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <WARNING>        nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```
And nm-ap photo:
[IMG]http://img279.imageshack.us/img279/8113/ubuntuvu2.png[/IMG]

Something is wrong ... when I run ```
iwlist ath0 scan
``` it show my two available APs. 

Next I tried wifi-radar. It show my two available APs:
[img]http://7thguard.net/files/przeglad_wifi/wifiradar_th.png[/img](example photo ), but I can't connect. They  use WPA, but I can't configure it :(

Why network-manager don't show my APs? It's problem with my card or with WPA configuration? How can I configure WPA ( with GUI;))? Please help me

---

