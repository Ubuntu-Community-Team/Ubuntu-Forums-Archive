---
title: "Wireless connects successfully but not working"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by genbuntu on 2008-06-23
Hello 

I'm having problems with my wireless connection through Ubuntu (Hardy). I can connect successfully to my home wifi router but I can neither browse nor ping anything (tried google and router ip) . The wired lan works fine though.
My wireless card in the laptop is pretty common and I did not notice any problems with Ubuntu Feisty . Nor did I ever require / manually install any sort of restricted drivers. Here are the specs from "lshw" command: 

```
description: Wireless interface
                product: PRO/Wireless 2915ABG Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes 

```

From what I've troubleshooted , the problem seem to lie in some setting / configuration in Ubuntu (Hardy) because when I boot into WinXP , it works fine. 
Any ideas / suggestions ? :)

---

### Post by superprash2003 on 2008-06-23
please post your ifconfig and iwconfig output

---

### Post by genbuntu on 2008-06-23
Thx for the reply :) .
When I'm on wired :

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe20::80e:b0ef:efb0:6e49/46 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1703036 (1.6 MB)  TX bytes:331935 (324.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67620 (66.0 KB)  TX bytes:67620 (66.0 KB)

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

When I turn on wireless :

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe20::80e:b0ef:efb0:6e49/46 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1731832 (1.6 MB)  TX bytes:341381 (333.3 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe20::80e:b0ef:efb0:6e49/46 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:1 dropped:1 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14940 (14.5 KB)  TX bytes:2069 (2.0 KB)
          Interrupt:22 Base address:0x2000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67620 (66.0 KB)  TX bytes:67620 (66.0 KB)

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ces"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-47 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:10

```

---

### Post by superprash2003 on 2008-06-23
its better to disconnect wired when trying wireless and vice versa

---

