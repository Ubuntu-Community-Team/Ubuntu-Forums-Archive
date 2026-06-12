---
title: "NetworkManager Won't Even Start"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by frioux on 2008-11-01
I can't seem to find any information at all about what's causing this.  Here is my console output:

```
localhost [8105] % sudo NetworkManager --no-daemon                    
NetworkManager: <info>  starting...
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch
NetworkManager: <info>  eth0: driver is '8139too'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_11_d8_c9_0b_89
NetworkManager: <info>  eth1: driver is 'ipw2200'.
NetworkManager: <info>  eth1: driver supports SSID scans (scan_capa 0x21).
NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'.
NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_12_f0_21_e6_85
NetworkManager: symbol lookup error: NetworkManager: undefined symbol: nm_connection_new_from_hash

```

Does anyone know what I need to do to fix this?  As far as I can tell it will be a huge hassle to get my wireless working without NM...

Thanks!

-fREW

---

### Post by jr72 on 2008-12-29
Have you tried WICD?

---

### Post by kevdog on 2008-12-29
Do you have any way of connecting to the internet now so you can download wicd, or do need to make a manual connection first just to establish and ip address?

---

