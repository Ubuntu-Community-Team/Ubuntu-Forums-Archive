---
title: "LAN connection keeps dropping randomly"
date: 2019-01-30
forum: Networking &amp; Wireless
---

### Post by iiidefconiii on 2019-01-30
Hi i have this question, my Ubuntu system keeps loosing internet connection until i reboot the system, i am a bit of a Linux noob and i do not know where to look for logs, or where to start.
All other devices in LAN are normally connected
-- Problem startted a few weeks ago, to bad i do not know from which date
-- I am getting a question mark symbol on my network when this happens. 
-- I already tried static IP, DNS and Gateway settings but that doesn't seem to solve it and i prefer having DHCP doing its thing
-- Even when i reboot the router the system is not getting back online, only a hard restart, any help would be appreciated.
-- I am running Ubuntu 18.04

If any more information is need please let me know so i can upload this.

ip link show
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 6c:62:6d:8f:a1:66 brd ff:ff:ff:ff:ff:ff
3: wlx485d60197bf6: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 48:5d:60:19:7b:f6 brd ff:ff:ff:ff:ff:ff


netstat -i
> Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp3s0    1500    31358      0      2 0         34017      0      0      0 BMRU
lo       65536    47912      0      0 0         47912      0      0      0 LRU

/sbin/ifconfig -a
> enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.3.1.2  netmask 255.255.255.0  broadcast 10.3.1.255
        inet6 fe80::6e62:6dff:fe8f:a166  prefixlen 64  scopeid 0x20<link>
        ether 6c:62:6d:8f:a1:66  txqueuelen 1000  (Ethernet)
        RX packets 34365  bytes 10096737 (10.0 MB)
        RX errors 0  dropped 2  overruns 0  frame 0
        TX packets 35814  bytes 6392389 (6.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 49667  bytes 37483110 (37.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 49667  bytes 37483110 (37.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx485d60197bf6: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 48:5d:60:19:7b:f6  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


ip -r
> default via 10.3.1.200 dev enp3s0 proto static metric 100 
10.3.1.0/24 dev enp3s0 proto kernel scope link src 10.3.1.2 metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 


lspci | egrep -i --color 'network|ethernet'
> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

### Post by iiidefconiii on 2019-01-30
I believe this is the solution if anyone else need it
[https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

---

