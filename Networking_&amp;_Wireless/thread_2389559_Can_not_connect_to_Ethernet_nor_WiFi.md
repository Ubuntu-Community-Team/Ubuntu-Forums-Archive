---
title: "Can not connect to Ethernet nor WiFi"
date: 2018-04-18
forum: Networking &amp; Wireless
---

### Post by eanej on 2018-04-18
Hi,

I installed Ubuntu 17.10 today from a "live" CD and during the installation, I was able to connect to the WiFi via TP-link USB Stick (tl-wn823n). Right now when Ubuntu is installed, I can not connect to ethernet nor WiFi.

I see available wifi hotspots around, but when i try to connect to them it says: "activation of netowrk connection failed ".

Result of:
**[ip a]("https://prnt.sc/j6wvpm")**
[NetworkManager.conf]("https://prnt.sc/j6wzgf")

I'm sorry about the screenshots, but I don't have a USB stick around to copy the text :-(

Thank you for any help :-)

---

### Post by zlb323 on 2018-04-18
Hello,

Can you post the results of these commands?

```
ifconfig
route
cat /etc/network/interfaces
```

---

### Post by eanej on 2018-04-20
[FONT=arial]Thank you for a reply, the WiFi USB stick suddenly started to work, but the internet is extremly slow (but maybe the wifi hotspot is to blame), but I would be super happy to use the ethernet connection anyway.

It says: "Wired connecting" for quite long time (~1-2 minutes) but does not connect


I think that the RX errors might mean that the driver is not working? I have[/FONT] **NVIDIA Corporation MCP61 Ethernet (rev a2)** card, is there some working driver for this card now? I've found this [thread]("https://askubuntu.com/questions/383426/trying-to-install-nvidia-corporation-mcp61-ethernet-ubuntu-13-04") but it does not really help.[FONT=arial]



ifconfig:[/FONT]
[FONT=arial]
[/FONT]
```
[FONT=arial]
[/FONT]
[FONT=arial]enp0s7: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 70:85:c2:6a:bd:4a  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 653  dropped 0  overruns 652  frame 1
        TX packets 89  bytes 13932 (13.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 684  bytes 45980 (45.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 684  bytes 45980 (45.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx503eaa36cf81: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.0.113  netmask 255.255.255.0  broadcast 172.16.0.255
        inet6 fe80::933e:33d4:89d0:fc61  prefixlen 64  scopeid 0x20<link>
        ether 50:3e:aa:36:cf:81  txqueuelen 1000  (Ethernet)
        RX packets 374  bytes 254302 (254.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 267  bytes 28913 (28.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]route:[/FONT]
```
[FONT=arial]
[/FONT]
[FONT=arial]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    600    0        0 wlx503eaa36cf81
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 wlx503eaa36cf81
172.16.0.0      0.0.0.0         255.255.255.0   U     600    0        0 wlx503eaa36cf81
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]cat /etc/network/interfaces[/FONT]
```
[FONT=arial]
[/FONT]
[FONT=arial]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
[/FONT]

```

---

