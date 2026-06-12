---
title: "Hannord USB 3.0 to Ethernet Adapter"
date: 2022-11-25
forum: Networking &amp; Wireless
---

### Post by jacqpret on 2022-11-25
Good Day

I purchased a Hannord USB 3.0 to Ethernet Adapter, Driver Free 10/100/1000 Mbps Network RJ45 LAN Wired Gigabit Ethernet Adapter as my onboard adapter is only 100Mbps on my Lenovo ideapad 100 
I installed it with a CAT6e to my Tenda Router on the a USB 3.0 port Ubuntu Budgie detects it as a Realtek RTL8152 but I only connect at 100Mbps to my 200Mbps network.
Please assist- how I can connect faster.

Regards
Jacques

---

### Post by TheFu on 2022-11-25
The Realtek RTL8152 is listed as a fast ethernet adapter, not GigE.  If the driver supports only 100Mbps connections, you won't go any faster.  So, step one is to determine the real chip inside and force that driver to be loaded, blacklisting the RTL8152 driver.

Reported connection speeds in a GUI mean nothing.  If you use iperf3 between 2 systems on the LAN, what speeds are reported?  I'd suggest using 'lsusb' to get the device ID and looking up the actual chip using that usb-id.

Does 'ip a' show a connection speed?  qlen is the part you want. ethtool can be useful for forcing speeds, assuming the driver supports faster.

---

### Post by jacqpret on 2022-11-25
[IMG]https://media.takealot.com/covers_tsins/55026044/55026044-1-pdpxl.jpg[/IMG]

Thank You, this is the results I get:

```
jacquesepretorius@ubuntu ~  
&#9584;&#9472;&#10148;  lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. RTL8723B Bluetooth
Bus 002 Device 005: ID 04f2:b572 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 012: ID 0bda:8152 Realtek Semiconductor Corp. RTL8152 Fast Ethernet Adapter
Bus 002 Device 002: ID 062a:4c01 MosArt Semiconductor Corp. 2,4Ghz Wireless Transceiver [for Delux M618 Plus Wireless Vertical Mouse]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
&#9581;&#9472;jacquesepretorius@ubuntu ~  
&#9584;&#9472;&#10148;  ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether c8:5b:76:c7:93:c8 brd ff:ff:ff:ff:ff:ff
4: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether c8:3d:d4:74:9f:a1 brd ff:ff:ff:ff:ff:ff
5: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:e3:66:8d brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
6: anbox0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 7a:54:23:24:b4:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.250.1/24 scope global anbox0
       valid_lft forever preferred_lft forever
8: enx00e04c360022: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:e0:4c:36:00:22 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.94/24 brd 192.168.1.255 scope global dynamic noprefixroute enx00e04c360022
       valid_lft 86197sec preferred_lft 86197sec
    inet6 fe80::951c:af3c:9e86:b318/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

---

### Post by TheFu on 2022-11-25
RTL8152 Fast Ethernet Adapter [https://devicehunt.com/view/type/usb/vendor/0BDA/device/8152](https://devicehunt.com/view/type/usb/vendor/0BDA/device/8152) is not GigE.
Seems you've been lied to by marketing.  Return it.

---

