---
title: "Conflicting information being reported for RTL8125 2.5Gb, not getting full speeds"
date: 2024-03-21
forum: Networking &amp; Wireless
---

### Post by jigmcgalliger on 2024-03-21
Hello all! I've had this node running for a while but I'm now trying to figure out some networking quirks that I've been ignoring. I'm using Ubuntu 22.04.4 LTS with an RTL8125 on the motherboard and suing a Windows 10 workstation with a SD-PEX24066 NIC using the same RTL8125 chipset to test the speeds. The switch is a QNAP QSW-1105-5T with their latest firmware, both using cat 6 cables. I've set the MTU to 9000 via netplan and the config sets 9000 on boot. I'm not getting the speeds I was expecting and Ubuntu is reporting conflicting info.


Here is the bidirectional iperf (similar speeds regardless of who is server/client):
Ubuntu:
```
~# iperf3 -c 192.168.1.175 -bidir
Connecting to host 192.168.1.175, port 5201
[  5] local 192.168.1.174 port 57786 connected to 192.168.1.175 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   195 MBytes  1.64 Gbits/sec    0    158 KBytes
[  5]   1.00-2.00   sec   198 MBytes  1.66 Gbits/sec    0    158 KBytes
[  5]   2.00-3.00   sec   179 MBytes  1.50 Gbits/sec    0    158 KBytes
[  5]   3.00-4.00   sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
[  5]   4.00-5.00   sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
[  5]   5.00-6.00   sec   165 MBytes  1.39 Gbits/sec    0    158 KBytes
[  5]   6.00-7.00   sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
[  5]   7.00-8.00   sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
[  5]   8.00-9.00   sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
[  5]   9.00-10.00  sec   165 MBytes  1.38 Gbits/sec    0    158 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.69 GBytes  1.45 Gbits/sec    0             sender
[  5]   0.00-10.00  sec  1.69 GBytes  1.45 Gbits/sec                  receiver

```
Windows:
```

Accepted connection from 192.168.1.174, port 57776
[  5] local 192.168.1.175 port 5201 connected to 192.168.1.174 port 57786
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-1.00   sec   188 MBytes  1.57 Gbits/sec
[  5]   1.00-2.00   sec   198 MBytes  1.66 Gbits/sec
[  5]   2.00-3.00   sec   179 MBytes  1.51 Gbits/sec
[  5]   3.00-4.00   sec   165 MBytes  1.39 Gbits/sec
[  5]   4.00-5.00   sec   165 MBytes  1.39 Gbits/sec
[  5]   5.00-6.00   sec   165 MBytes  1.39 Gbits/sec
[  5]   6.00-7.00   sec   165 MBytes  1.38 Gbits/sec
[  5]   7.00-8.00   sec   165 MBytes  1.39 Gbits/sec
[  5]   8.00-9.00   sec   165 MBytes  1.39 Gbits/sec
[  5]   9.00-10.00  sec   165 MBytes  1.38 Gbits/sec
[  5]  10.00-10.04  sec  5.74 MBytes  1.38 Gbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-10.04  sec  0.00 Bytes  0.00 bits/sec                  sender
[  5]   0.00-10.04  sec  1.69 GBytes  1.44 Gbits/sec                  receiver

```

Ubuntu NIC showing conflicting info for rated speeds, not sure what to trust:
```

~# ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp42s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 2c:f0:5d:7c:91:20 brd ff:ff:ff:ff:ff:ff
    
~# inxi -n
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169
  IF: enp42s0 state: up speed: 2500 Mbps duplex: full mac: 2c:f0:5d:7c:91:20
  
~# lshw -class network
  *-network
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:2a:00.0
       logical name: enp42s0
       version: 04
       serial: 2c:f0:5d:7c:91:20
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-97-generic duplex=full firmware=rtl8125b-2_0.0.2 07/13/20 ip=192.168.1.174 latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:35 ioport:f000(size=256) memory:fc500000-fc50ffff memory:fc510000-fc513fff


~# mii-tool -v enp42s0
enp42s0: negotiated 1000baseT-FD flow-control, link ok
  product info: vendor 00:e0:4c or 00:07:32, model 4 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control


~# ethtool enp42s0
Settings for enp42s0:
        Supported ports: [ TP    MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
                                2500baseT/Full
        Supported pause frame use: Symmetric Receive-only
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
                                2500baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Half 1000baseT/Full
                                             2500baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Link partner advertised FEC modes: Not reported
        Speed: 2500Mb/s
        Duplex: Full
        Auto-negotiation: on
        master-slave cfg: preferred slave
        master-slave status: slave
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: external
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: d
        Link detected: yes

```
The Windows workstation has the following enabled: jumbo frame, 2.5G full duplex, large send offload enabled, and receive/transmit buffer is 512. It also shows MTU of 9198:
```
>netsh interface ipv4 show subinterface


   MTU  MediaSenseState   Bytes In  Bytes Out  Interface
------  ---------------  ---------  ---------  -------------
  9198                1        nnn        nnn  Ethernet


```
Does anyone have an idea as to why the Ubuntu server is showing conflicting info and what I am missing to reach full speeds?

Thanks!

---

### Post by TheFu on 2024-03-21
You need to have your frames fit inside the frame limitations of all the hardware.  Many devices that say "jumbo frame support" don't mean 9001 bytes. They mean 9000 bytes, so any number higher than that will be split into 2 packets.  I don't know exactly what each of the devices you use limits are. They need to be checked.

Also, I'd check that the tools you are using aren't OOS and are actually capable of reporting speeds higher than 1 Gbps.  For example, I think mii-tool is part of net-tools, which hasn't been supported since 2011.

I think there's a limitation on CAT6 cable length for bandwidth depending on the performance. While it is unlikely that is being surpassed, while you are looking up specs, check that.  CAT6 and CAT6a aren't the same, so be certain you have the exact spec of the cable used AND of the connectors, if you built the cables yourself.

---

### Post by praseodym on 2024-03-22
```
driver=r8169
```?!

Please show

```
lsmod
```

---

### Post by TheFu on 2024-03-22
I googled a bit this morning and found a few articles on blogs that I've never seen before about downloading the correct drivers from RealTek, compiling them and installing them.  Neither seemed to use a PPA or DKMS, which are methods that make ongoing maintenance easier.  Basically, they fix the problem once and every new kernel, you'll need to manually (or script) the relink and re-load of the drivers.

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)
was the place to get the drivers.

I've been avoiding Realtek for about 10 yrs now due to this sort of issue. Intel NICs kinda "just work".  On your next system, of when the RealTek NIC dies, consider getting a replacement from Intel.  The $5-$10 extra cost will save you lots of frustration.

---

### Post by jigmcgalliger on 2024-03-22
> **TheFu said:**
> You need to have your frames fit inside the frame limitations of all the hardware.  Many devices that say "jumbo frame support" don't mean 9001 bytes. They mean 9000 bytes, so any number higher than that will be split into 2 packets.  I don't know exactly what each of the devices you use limits are. They need to be checked.

Also, I'd check that the tools you are using aren't OOS and are actually capable of reporting speeds higher than 1 Gbps.  For example, I think mii-tool is part of net-tools, which hasn't been supported since 2011.

I think there's a limitation on CAT6 cable length for bandwidth depending on the performance. While it is unlikely that is being surpassed, while you are looking up specs, check that.  CAT6 and CAT6a aren't the same, so be certain you have the exact spec of the cable used AND of the connectors, if you built the cables yourself.

Windows is now set to 9000 MTU:
```

> netsh interface ipv4 show subinterface


   MTU  MediaSenseState   Bytes In  Bytes Out  Interface
------  ---------------  ---------  ---------  -------------
  9000                1        nnn       nnn      Ethernet

```
From Ubuntu:
```

~# ping 192.168.1.175 -c 2 -M do -s 8972
PING 192.168.1.175 (192.168.1.175) 8972(9000) bytes of data.
8980 bytes from 192.168.1.175: icmp_seq=1 ttl=128 time=0.351 ms
8980 bytes from 192.168.1.175: icmp_seq=2 ttl=128 time=0.711 ms

```
From Windows:
```
>ping -f -l 8972 192.168.1.174 -n 2
Pinging 192.168.1.174 with 8972 bytes of data:
Reply from 192.168.1.174: bytes=8972 time<1ms TTL=64
Reply from 192.168.1.174: bytes=8972 time<1ms TTL=64

```

Two of the cables are cat 6 RadioShack branded (throwback), I've tried other cat 5e ones as well. I didn't self-splice these ones.

Am I doing the above correct, so as to not fragment and send only 9000 bytes (including) headers?



> **praseodym said:**
> 
driver=r8169 ?!

Please show lsmod


Here you go:
```
~# lsmod |egrep 'r8169|Module'
Module                  Size  Used by
r8169                 102400  0
```

Hope this helps.

---

### Post by TheFu on 2024-03-23
> **jigmcgalliger said:**
>  

Here you go:
```
~# lsmod |egrep 'r8169|Module'
Module                  Size  Used by
r8169                 102400  0
```

Hope this helps.

The system has the wrong driver. You need the one for RTL8125.

---

### Post by jigmcgalliger on 2024-03-23
So I installed the 2.5G Ethernet LINUX driver r8125 [from Realtek]("https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software") with their readme instructions:
```

~/r8125-9.012.04# sudo ./autorun.sh

Check old driver and unload it.
rmmod r8169
Build the module and install
Skipping BTF generation for /root/r8125-9.012.04/src/r8125.ko due to unavailability of vmlinux
arch/x86/Makefile:142: CONFIG_X86_X32 enabled but no binutils support
Warning: modules_install: missing 'System.map' file. Skipping depmod.
DEPMOD 5.15.0-101-generic
load module r8125
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-5.15.0-101-generic
Completed.

[after reboot with secure boot disabled]
~/r8125-9.012.04# lsmod |egrep 'r8169|Module|r8125'
Module                  Size  Used by
r8125                 278528  0

~/r8125-9.012.04# inxi -n
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8125
  IF: enp42s0 state: up speed: 2500 Mbps duplex: full mac: 2c:f0:5d:7c:91:20


```

For some reason this only loads when secure boot is disabled. Any reason as to why that is?

Also, still getting the same speeds as before:
```

Accepted connection from 192.168.1.174, port 33246
[  5] local 192.168.1.175 port 5201 connected to 192.168.1.174 port 33256
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-1.00   sec   191 MBytes  1.60 Gbits/sec
[  5]   1.00-2.00   sec   191 MBytes  1.61 Gbits/sec
[  5]   2.00-3.00   sec   165 MBytes  1.38 Gbits/sec
[  5]   3.00-4.00   sec   165 MBytes  1.38 Gbits/sec
[  5]   4.00-5.00   sec   164 MBytes  1.38 Gbits/sec
[  5]   5.00-6.00   sec   165 MBytes  1.38 Gbits/sec
[  5]   6.00-7.00   sec   164 MBytes  1.38 Gbits/sec
[  5]   7.00-8.00   sec   164 MBytes  1.38 Gbits/sec
[  5]   8.00-9.00   sec   165 MBytes  1.38 Gbits/sec
[  5]   9.00-10.00  sec   165 MBytes  1.38 Gbits/sec
[  5]  10.00-10.04  sec  6.46 MBytes  1.38 Gbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-10.04  sec  0.00 Bytes  0.00 bits/sec                  sender
[  5]   0.00-10.04  sec  1.67 GBytes  1.43 Gbits/sec                  receiver

```


Any ideas?

---

### Post by TheFu on 2024-03-24
Secure boot requires signed code.  By using a driver you downloaded directly, I think that chain got broken.  I've never used secure boot and barely use UEFI booting, so I'm not the expert on these things.

Is your switch 2.5Gbps capable?  Do other devices using it achieve that?
As I wrote already, I don't use Realtek stuff.

FYI, I don't think it is Ubuntu. I see plenty of throughput:
```
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  29.9 GBytes  25.7 Gbits/sec    0             sender
[  5]   0.00-10.04  sec  29.9 GBytes  25.6 Gbits/sec                  receiver
```

Check all the external parts in the connection one at a time, so it can be isolated.

---

