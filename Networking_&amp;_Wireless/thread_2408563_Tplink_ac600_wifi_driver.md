---
title: "Tplink ac600 wifi driver"
date: 2018-12-19
forum: Networking &amp; Wireless
---

### Post by jfca283 on 2018-12-19
Hello, 
I need some help for installing the driver for my Archer T2U V2.
I've downloaded the driver from here:
[https://www.tp-link.com/us/download/Archer-T2U.html#Driver](https://www.tp-link.com/us/download/Archer-T2U.html#Driver)
And when I run the sudo make, I've received this:
```
juan@juan-OptiPlex-7010:~/z$ sudo make
Makefile:31: /home/juan/z/os/linux/config.mk: No such file or directory
make: *** No rule to make target '/home/juan/z/os/linux/config.mk'.  Stop.

```

In case of help, this is my lsusb, uname -r and ifconfig
```
juan@juan-OptiPlex-7010:~/z$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:761a Ralink Technology, Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1a2c:2d23 China Resource Semico Co., Ltd 
Bus 003 Device 002: ID 0458:0186 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 004: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
juan@juan-OptiPlex-7010:~/z$ uname -r
4.15.0-42-generic
juan@juan-OptiPlex-7010:~/z$ ifconfig
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether b8:ca:3a:78:a4:53  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7100000-f7120000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 8760  bytes 691414 (691.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8760  bytes 691414 (691.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx002586e74a8f: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.102  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::505a:b40e:a3:98cd  prefixlen 64  scopeid 0x20<link>
        ether 00:25:86:e7:4a:8f  txqueuelen 1000  (Ethernet)
        RX packets 64010  bytes 68583220 (68.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 54113  bytes 8602538 (8.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

By the way, I'm using a wifi adaptor 2.4g .
Thanks for your time and interest.

---

### Post by wildmanne39 on 2018-12-19
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

