---
title: "Help, my wireless  card  AR9565 is not working(ubuntu 16.04)"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by danke on 2016-04-23
Hi all,
I have just finished the installation (ubuntu 16.04 ) and the wifi doesn't work well.
If I turn the wifi on and off several times or suspend my computer ,the wifi list on the top bar shows no wifi ,but in the System settings' Network ,the wifi are still there.
Worse still , sometimes, the Network settings tells me that I have turned the wireless hotspot on. if i turn it off ,the window will disappear.
Sometimes when I got the wifi connected , the icon of the network on the top bar become the icon of wired link,which are two arrows;
I am sorry for my poor english.
Any help very gratefully received.
Many thanks
In addition ,Windows 10 and Ubuntu 14.04 on the laptop worked fine.
Here are some information
```
                         gaoliang@gaoliang-X550JX:~$ lspci -nn | grep 0280

 03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)

    
```

```
gaoliang@gaoliang-X550JX:~$ ifconfig
enp4s0f1  Link encap:Ethernet  HWaddr 14:dd:a9:20:ab:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enxf6c60c068e2e Link encap:Ethernet  HWaddr f6:c6:0c:06:8e:2e  
          inet addr:192.168.42.103  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::c203:b465:9a6a:d3bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1892541 (1.8 MB)  TX bytes:889267 (889.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:153935 (153.9 KB)  TX bytes:153935 (153.9 KB)

wlp3s0    Link encap:Ethernet  HWaddr 28:c2:dd:46:e2:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2584 (2.5 KB)  TX bytes:9386 (9.3 KB)


```
thanks a lot

---

### Post by danke on 2016-04-23
In Addition ;
```
dmesg | grep wlp3s0
[    7.101414] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[   21.575656] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.587618] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   22.083401] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   22.956215] wlp3s0: authenticate with 00:17:7b:35:7e:05
[   22.968153] wlp3s0: send auth to 00:17:7b:35:7e:05 (try 1/3)
[   22.971577] wlp3s0: authenticated
[   22.974103] wlp3s0: associate with 00:17:7b:35:7e:05 (try 1/3)
[   22.981298] wlp3s0: RX AssocResp from 00:17:7b:35:7e:05 (capab=0x401 status=0 aid=3)
[   22.981380] wlp3s0: associated
[   22.981412] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   23.387209] wlp3s0: Limiting TX power to 27 (27 - 0) dBm as advertised by 00:17:7b:35:7e:05
[   27.046651] wlp3s0: authenticate with 00:17:7b:35:7f:31
[   27.064783] wlp3s0: send auth to 00:17:7b:35:7f:31 (try 1/3)
[   27.069758] wlp3s0: authenticated
[   27.073595] wlp3s0: associate with 00:17:7b:35:7f:31 (try 1/3)
[   27.076914] wlp3s0: RX AssocResp from 00:17:7b:35:7f:31 (capab=0x401 status=0 aid=2)
[   27.077011] wlp3s0: associated
[   27.215638] wlp3s0: Limiting TX power to 27 (27 - 0) dBm as advertised by 00:17:7b:35:7f:31
[   50.107368] wlp3s0: deauthenticating from 00:17:7b:35:7f:31 by local choice (Reason: 3=DEAUTH_LEAVING)
[   51.357105] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   51.398923] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   99.550556] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   99.600218] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  119.914448] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  119.946753] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  142.603676] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  142.618969] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  142.672293] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  147.443958] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  147.483786] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  161.422000] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  161.434475] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  161.488758] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  172.235615] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  172.264515] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  471.577267] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  471.589759] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  471.652308] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2202.335070] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2202.348089] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2202.441486] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2225.001289] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2225.039381] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2229.884871] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2229.926934] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready


```

---

### Post by Irihapeti on 2016-04-23
Unfortunately, I think you've run into the same bug that's affecting my Asus EeePC 900: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1569590](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1569590)

I can get mine to work by turning wifi off and on again with the function keys, but it sounds as though you've tried that and it's not reliable.

The only other thing I can think of is to uninstall network manager and replace it with wicd, but I can't be sure that it won't make a mess of your installation.

---

