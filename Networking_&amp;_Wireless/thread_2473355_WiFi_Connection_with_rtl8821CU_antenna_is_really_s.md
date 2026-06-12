---
title: "WiFi Connection with rtl8821CU antenna is really slow"
date: 2022-04-01
forum: Networking &amp; Wireless
---

### Post by draxavi on 2022-04-01
I have an 200Mb internet connection, in my notebook that have the same  distro as my PC (Ubuntu Studio) can get the expected speed (more than  100 Mbps in Speedtest by Ookla) but my PC is getting really low speeds  (1.72 Mbps). What can be the issue?  I tried to use [https://github.com/brektrou/rtl8821CU.git](https://github.com/brektrou/rtl8821CU.git) (Using just make install, I could not properly follow the instructions and change the name to wlan0)

lspci -knn | grep Net -A3
Results in nothing

```
ifconfig
enp7s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 24:4b:fe:0c:44:9e  txqueuelen 1000  (Ethernet) 
        RX packets 0  bytes 0 (0.0 B) 
        RX errors 0  dropped 0  overruns 0  frame 0 
        TX packets 0  bytes 0 (0.0 B) 
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536 
        inet 127.0.0.1  netmask 255.0.0.0 
        inet6 ::1  prefixlen 128  scopeid 0x10<host> 
        loop  txqueuelen 1000  (Local Loopback) 
        RX packets 11170  bytes 1117367 (1.1 MB) 
        RX errors 0  dropped 0  overruns 0  frame 0 
        TX packets 11170  bytes 1117367 (1.1 MB) 
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

wlxa0d768202865: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500 
        inet 192.168.15.9  netmask 255.255.255.0  broadcast 192.168.15.255 
        inet6 fe80::1de2:7cde:df2b:620f  prefixlen 64  scopeid 0x20<link> 
        inet6 2804:431:c7c7:7536:8c35:ab3:1a21:3813  prefixlen 64  scopeid 0x0<global> 
        inet6 2804:431:c7c7:7536:f1ba:8c18:e73:d5eb  prefixlen 64  scopeid 0x0<global> 
        ether a0:d7:68:20:28:65  txqueuelen 1000  (Ethernet) 
        RX packets 55617  bytes 37924703 (37.9 MB) 
        RX errors 0  dropped 3828  overruns 0  frame 0 
        TX packets 49658  bytes 18530245 (18.5 MB) 
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 003 Device 004: ID 18f8:0f97 [Maxxter] Optical Gaming Mouse [Xtrem] 
Bus 003 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller 
Bus 003 Device 002: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by draxavi on 2022-04-01
It's seems that the issue is that the adapter just have support to USB 2.0 I Plugged it in a 2.0 hub (that, by sheer luck I had just one functional in my old case)

---

### Post by slickymaster on 2022-04-04
*Thread moved to **Networking & Wireless**.*

---

### Post by morrownr on 2022-04-06
Hi draxavi

> rtl8821CU antenna

That seems to indicate you think you have a USB WiFi adapter based on the rtl8821cu chipset. To check that, don't use lspci, use:

lsusb

In fact, why don't you post the output of lsusb so we can check.

Here is a link to a more modern version of the driver for the 8821cu and it has extensive documentation:

[https://github.com/morrownr/8821cu-20210118](https://github.com/morrownr/8821cu-20210118)

You will need to uninstall any previously installed drivers prior to installing the above driver.

Regards

---

