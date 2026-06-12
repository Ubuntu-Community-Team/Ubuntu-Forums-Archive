---
title: "Wifi not working"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by devlin3 on 2016-05-16
Hello,

The wifi system I currently use once had two routers. The internet plugged into the modem via coaxial cable, the modem then went to a netgear router, which then went to a wireless router. Upon discovering this, I removed the netgear router, since every device used wifi. However, now my linux laptop will not connect to the wifi, although it can still connect via ethernet cable. How do I fix this?

Thank you.

---

### Post by Brij_Raj_Kishore on 2016-05-16
Post The Output of the command ```
ifconfig
``` & ```
rfkill list
```

---

### Post by devlin3 on 2016-05-21
sorry for the late reply, been very busy lately. 

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:5e:13:e4  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2605:e000:100d:4054:f2de:f1ff:fe5e:13e4/64 Scope:Global
          inet6 addr: 2605:e000:100d:4054:c1ba:28dd:fbe3:b651/64 Scope:Global
          inet6 addr: fe80::f2de:f1ff:fe5e:13e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319800 (319.8 KB)  TX bytes:89596 (89.5 KB)
          Interrupt:20 Memory:f2400000-f2420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125050 (125.0 KB)  TX bytes:125050 (125.0 KB)

wlan0     Link encap:Ethernet  HWaddr 18:3d:a2:34:e3:0c  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2605:e000:100d:4054:883d:5a40:a21e:c495/64 Scope:Global
          inet6 addr: fe80::1a3d:a2ff:fe34:e30c/64 Scope:Link
          inet6 addr: 2605:e000:100d:4054:1a3d:a2ff:fe34:e30c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297048 (297.0 KB)  TX bytes:310597 (310.5 KB)
```
rfkill list:
```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

