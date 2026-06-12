---
title: "Network is Unreachable - Wireless"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by Wiking on 2014-06-17
When I try to connect to my Wifi the network manager says I'm connected but I cannot login into my router nor can I ping my router. 

In the attached picture the red arrow points to the wifi icon, it displays as connected but with no waves.

Also another thing I noticed is that **wlan0** appears twice. Once as **wlan0** and another as **mon.wlan0**. What does that mean?

```
console:~$ ping 192.168.0.1
connect: Network is unreachable
```

```
console:~$ sudo lshw -C network   *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: aa:aa:aa:aa:aa:aa
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:51 memory:c0700000-c073ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: mon.wlan0
       version: 34
       serial: bb:bb:bb:bb:bb:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-20-generic firmware=18.168.6.1 ip=10.42.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:c0600000-c0601fff
console:~$ iwconfig
mon.wlan0  IEEE 802.11abgn  Mode:Monitor  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  Mode:Master  Tx-Power=15 dBm                                                                                                                                         
          Retry  long limit:7   RTS thr:off   Fragment thr:off                                                                                                                                  
          Power Management:on                                                                                                                                                                   
                                                                                                                                                                                                
console:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5309 (5.3 KB)  TX bytes:5309 (5.3 KB)


mon.wlan0 Link encap:UNSPEC  HWaddr BB-BB-BB-BB-BB-BB-BB-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:897580 (897.5 KB)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr bb:bb:bb:bb:bb:bb  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: ****::****:****:****:****/68 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10055 (10.0 KB)
```

---

### Post by bigdigdgs-s on 2014-11-06
Got similar thing on my laptop with ubuntu 14.04.
i've changed my router and gave same ssid to access point as previous AP has.
And... every device at home have an internet connection, even this laptop have it under windows, but under ubuntu nothing, can't reach even 192.168.0.1

---

### Post by chili555 on 2014-11-06
The answer in the case above is fairly obvious:> wlan0     IEEE 802.11abgn  [COLOR="#FF0000"]Mode:Master[/COLOR]  Tx-Power=15 dBm                                                                                                                                         
          Retry  long limit:7   RTS thr:off   Fragment thr:off                                                                                                                                  
          Power Management:on      The card needs to be in Managed mode, not Master. 

What are your details?```
lspci -nn | grep 0280
iwconfig
rfkill list all
```

---

