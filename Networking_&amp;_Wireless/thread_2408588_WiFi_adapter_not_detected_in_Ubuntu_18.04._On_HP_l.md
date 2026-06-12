---
title: "WiFi adapter not detected in Ubuntu 18.04. On HP laptop 15-af115ns"
date: 2018-12-20
forum: Networking &amp; Wireless
---

### Post by valrax on 2018-12-20
Hello,
I recently installed ubuntu 18.04. The problem I have is that the WiFi adapter isn't detected.

```
 lspci | grep -i network
02:00.0 Network controller: Broadcom Limited BCM43142 802.11b/g/n (rev 01) 
```

```
 ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.159  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6dd9:b345:2442:96a0  prefixlen 64  scopeid 0x20<link>
        ether 94:57:a5:e7:64:ec  txqueuelen 1000  (Ethernet)
        RX packets 200279  bytes 285396290 (285.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 123349  bytes 9847070 (9.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 103752  bytes 109512929 (109.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 103752  bytes 109512929 (109.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 
```

```
 uname -r4.15.0-42-generic 
```

I have tried some solutions that worked for users, but it didn't work for me. Can you help me?

Thanks

---

### Post by jeremy31 on 2018-12-20
What is results for ```
 lspci -nnk | grep -iA3 net; mokutil --sb-state 
```

---

### Post by valrax on 2018-12-20
This is what I got:
```
 lspci -nnk | grep -iA3 net; mokutil --sb-state
02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel modules: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:80cb]
    Kernel driver in use: r8169
    Kernel modules: r8169
SecureBoot enabled 
```

---

### Post by jeremy31 on 2018-12-20
Go into BIOS settings and disable Secure Boot

---

### Post by valrax on 2018-12-20
I disabled it and works!! Thanks! I tried a lot of things

---

