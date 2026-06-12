---
title: "Netkit issue"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by code+anime on 2018-03-30
[COLOR=#2C2C2C][FONT=Open Sans]I try the ifconfig eth0 command but it says eth0 not found. I tried changing the contents of the /etc/network/interfaces to auto eth0 (in the ubuntu terminal), but when i restart networking services using etc/init.d/networking it says eth0 device not found.[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=Open Sans]I'm not sure what the issue is TBH, and how to get it working in netkit so I can do my work...[/FONT][/COLOR]

---

### Post by chili555 on 2018-03-30
Because of predictable interface naming, your ethernet interface may not be eth0 in recent Ubuntu versions: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Instead of running:```
ifconfig eth0
```Rather, I suggest you simply run:```
ifconfig
```On my machine, as an example, it returns:```
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether xx:f7:28:ae:83:xx  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe0600000-e0620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3858  bytes 305748 (305.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3858  bytes 305748 (305.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.120  netmask 255.255.252.0  broadcast 192.168.3.255
        inet6 2600:1700:5aa0:839:e48c:295c:6c07:b141  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::e28a:5920:5ed5:d892  prefixlen 64  scopeid 0x20<link>
        ether xx:c5:d4:0e:64:xx txqueuelen 1000  (Ethernet)
        RX packets 406959  bytes 567432474 (567.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 107415  bytes 14623382 (14.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```My ethernet interface is enp0s25; roughly, that signifies **E**ther**N**et **P**ci interface.

I suggest that you revert the changes you made to /etc/network/interfaces.

---

