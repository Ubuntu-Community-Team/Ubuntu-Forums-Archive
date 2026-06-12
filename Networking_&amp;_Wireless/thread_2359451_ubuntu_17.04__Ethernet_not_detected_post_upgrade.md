---
title: "ubuntu 17.04 : Ethernet not detected post upgrade"
date: 2017-04-24
forum: Networking &amp; Wireless
---

### Post by sivabalan19 on 2017-04-24
Hi All,

I recently upgraded to ubuntu 17.04. But found my wired network is not detected post upgrade. Wireless is working fine. Googling didnt help me much. Below are the some of more information that i could provide. I didn't install any of the driver. My laptop is Dell Latitude e5450. Can you please help me to fix the problem ?

I find the network interface is been disabled inlshw result (but still do not know how to enable it:(). Let me know if you need more information. 

```
ifconfig -a
eno1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 20:47:47:af:96:f8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7200000-f7220000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1112  bytes 72838 (72.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1112  bytes 72838 (72.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.209.233  netmask 255.255.252.0  broadcast 192.168.211.255
        inet6 fe80::cd27:5b5f:400a:cc03  prefixlen 64  scopeid 0x20<link>
        ether 5c:e0:c5:21:45:a8  txqueuelen 1000  (Ethernet)
        RX packets 19189  bytes 12608246 (12.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13287  bytes 5452392 (5.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```


```
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```


```
 sudo lshw -C network
  *-network DISABLED        
       description: Ethernet interface
       product: Ethernet Connection (3) I218-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 03
       serial: 20:47:47:af:96:f8
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7200000-f721ffff memory:f7243000-f7243fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 59
       serial: 5c:e0:c5:21:45:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-19-generic firmware=22.391740.0 ip=192.168.209.233 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:49 memory:f7000000-f7001fff
```



-Thanks,
Siva V

---

### Post by howefield on 2017-04-24
Thread moved to the "*Networking & Wireless*" forum for a better fit and code tags added.

---

### Post by sivabalan19 on 2017-05-03
Hi all,

I am still not lucky to fix this. Any help would be great.

---

### Post by jeremy31 on 2017-05-03
Have you tried```
sudo ifconfig eno1 up
```

---

