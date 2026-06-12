---
title: "Enable Ethernet, Wi-Fi and mobile network simultaneously"
date: 2021-02-24
forum: Networking &amp; Wireless
---

### Post by shamanthnorway on 2021-02-24
Hi All,

We are using Ubuntu 18.04LTS and I am trying to figure out how to maintain all the connections – Ethernet, Wi-fi and cellular to be active at the same time. That is, we must be able to SSH/VNC to the system using any of the 3 IP addresses.  
 
**Current configuration**:

[LIST]
[*]Ethernet, Wi-fi and cellular connections are enabled. 
[*]Therefore, when a ethernet cable is connected, only ethernet is active. 
[*]When ethernet is disconnected, Wi-fi is active. 
[*]Similarly, when wi-fi is disabled, cellular connection is active. _Note: We are not able to enable VNC/desktop sharing for cellular connection_ 
[/LIST]
 

More information of required interfaces are 

[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]Type[/TD]
[TD]interface name[/TD]
[TD]IP address[/TD]
[TD]gateway[/TD]
[/TR]
[TR]
[TD]Ethernet[/TD]
[TD]enp2s0[/TD]
[TD]192.168.17.10[/TD]
[TD]192.168.17.98[/TD]
[/TR]
[TR]
[TD]Mobile Broadband[/TD]
[TD]ppp0[/TD]
[TD]10.165.3.242[/TD]
[TD]0.0.0.0 (hope that this is not an issue)[/TD]
[/TR]
[TR]
[TD]Wi-fi[/TD]
[TD]wlp1s0[/TD]
[TD]10.85.3.144[/TD]
[TD]10.85.0.1[/TD]
[/TR]
[/TABLE]
All connections use DHCP

Any recommendations/advise will be appreciated.

Result of `ifconfig -a`
```

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.17.10  netmask 255.255.255.0  broadcast 192.168.17.255
        inet6 fe80::c83f:c078:6434:e9b4  prefixlen 64  scopeid 0x20<link>
        inet6 fdae:5dac:ede9:1:d08:3e86:ff87:639b  prefixlen 64  scopeid 0x0<global>
        inet6 fdae:5dac:ede9:1:44a0:25b7:5b4b:1987  prefixlen 64  scopeid 0x0<global>
        ether 00:07:32:5f:bb:69  txqueuelen 1000  (Ethernet)
        RX packets 29804  bytes 10197574 (10.1 MB)
        RX errors 0  dropped 2  overruns 0  frame 0
        TX packets 52440  bytes 50542246 (50.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 763  bytes 64001 (64.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 763  bytes 64001 (64.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.165.3.242  netmask 255.255.255.255  destination 0.0.0.0
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 5  bytes 62 (62.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 26  bytes 841 (841.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.85.3.144  netmask 255.255.240.0  broadcast 10.85.15.255
        inet6 fe80::3de5:5c8b:c24a:7b32  prefixlen 64  scopeid 0x20<link>
        ether cc:4b:73:5a:52:78  txqueuelen 1000  (Ethernet)
        RX packets 29861  bytes 43962791 (43.9 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 4477  bytes 343709 (343.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wwp0s21f0u7u1i4: flags=4226<BROADCAST,NOARP,MULTICAST>  mtu 1500
        ether 36:3a:f6:ba:f7:08  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Result of `netstat -rn`
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.17.98   0.0.0.0         UG        0 0          0 enp2s0
0.0.0.0         10.85.0.1       0.0.0.0         UG        0 0          0 wlp1s0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
10.85.0.0       0.0.0.0         255.255.240.0   U         0 0          0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp1s0
192.168.17.0    0.0.0.0         255.255.255.0   U         0 0          0 enp2s0

```

---

### Post by howefield on 2021-02-25
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by shamanthnorway on 2021-02-25
Thank you

---

