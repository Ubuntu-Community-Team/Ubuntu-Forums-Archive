---
title: "Network Manager Freezes when I try and activate my wireless"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by tartarian on 2007-07-05
I'm trying to connect to the internet with a Belkin wireless USB adapter (UR054g)
I've got the adapter to be recognised and its scanning and finding the available networks
but when I open network manager, set it as active/modify the properties my entire system frezzes and I have to pull the power. It also does this when I run the cmd "sudo /etc/init.d/networking restart"

Here is the output of hopefully all the relevant files:

ifconfig:
```


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1820 (1.7 KiB)  TX bytes:1820 (1.7 KiB)

rausb0    Link encap:Ethernet  HWaddr 00:11:50:4C:37:C8  
          inet6 addr: fe80::211:50ff:fe4c:37c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1268029 (1.2 MiB)  TX bytes:79872 (78.0 KiB)

```
iwconfig:
```


rausb0    RT2500USB WLAN  ESSID:"WANADOO-3EB4"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-207 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwlist scan:

```


rausb0    Scan completed :
          Cell 01 - Address: 00:0E:9B:A2:14:1C
                    Mode:Managed
                    ESSID:"WANADOO-3EB4"
                    Encryption key:on
                    Channel:1
          Cell 02 - Address: 00:14:6C:94:34:AA
                    Mode:Managed
                    ESSID:"Foster1"
                    Encryption key:on
                    Channel:1
          Cell 03 - Address: 00:13:49:A0:DE:94
                    Mode:Managed
                    ESSID:"ZyXEL"
                    Encryption key:off
                    Channel:6
          Cell 04 - Address: 00:18:4D:44:FC:B6
                    Mode:Managed
                    ESSID:"NETGEAR"
                    Encryption key:on
                    Channel:11

```
/etc/network/interfaces:

```


auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp
#wireless-essid WANADOO-3EB4
#wireless-key 962341B24DAF56AD0966AB5B38

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid WANADOO-3EB4
wireless-key 962341B24DAF56AD0966AB5B38

```

Any ideas?
All help greatly appreciated :)
Thanks!

---

