---
title: "Intel 1217-V...  No DHCP, no network even with static IP."
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by bjacques123 on 2016-04-04
Hi all.  I'm running into this odd behavior with the built-in Intel 1217-V NIC on my motherboard...  Initially manifested as an inability to gain an IP address via DHCP, even when the Windows 10 partition on the same machine is working normally.  My initial troubleshooting step was to set a static IP address on the NIC.  Well, that's where it got really odd...  Pings to default gateway, or other hosts on the LAN go unanswered.  Running wireshark one of the other LAN hosts, I don't see the echo requests from the errant Ubuntu machine.

Now another interesting datapoint is that ARP requests are typically "incomplete".  Though sometimes it seems to resolve ARP, when I try to ping that IP, I get no response, and the ARP entry goes back to incomplete:

```
brendan@brendan-linux:~$ ping 192.168.0.152PING 192.168.0.152 (192.168.0.152) 56(84) bytes of data.
From 192.168.0.8 icmp_seq=1 Destination Host Unreachable
From 192.168.0.8 icmp_seq=2 Destination Host Unreachable
From 192.168.0.8 icmp_seq=3 Destination Host Unreachable
From 192.168.0.8 icmp_seq=4 Destination Host Unreachable
From 192.168.0.8 icmp_seq=5 Destination Host Unreachable
From 192.168.0.8 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.0.152 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7030ms
pipe 3
brendan@brendan-linux:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.152                    (incomplete)                              eth0
192.168.0.1              ether   48:5d:36:7e:4d:b1   C                     eth0
brendan@brendan-linux:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.8 icmp_seq=1 Destination Host Unreachable
From 192.168.0.8 icmp_seq=2 Destination Host Unreachable
^C
--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3016ms
pipe 2
brendan@brendan-linux:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.152                    (incomplete)                              eth0
192.168.0.1                      (incomplete)                              eth0



```

But the underlying hardware seems to be just fine:
```
brendan@brendan-linux:~$ sudo lshw -numeric -C network  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V [8086:153B]
       vendor: Intel Corporation [8086]
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 74:d0:2b:c4:85:e0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:ef200000-ef21ffff memory:ef238000-ef238fff ioport:f040(size=32)
brendan@brendan-linux:~$ sudo dmesg | grep eth0
[    0.724619] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.724621] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 74:d0:2b:c4:85:e0
[    0.724623] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.724659] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[   12.838247] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  216.458672] device eth0 entered promiscuous mode
[  272.099125] device eth0 left promiscuous mode

```

As seen above in the dmesg output, I even did a tcpdump on the interface...  That's an interesting one.  When set to promiscuous mode, the NIC certainly does see frames (broadcasts and multicasts, etc).  It's almost as if something is inhibiting the NIC from actually putting bits on the wire.

At this point, I'm at a loss, can anyone out there help me with next troubleshooting steps?

Thanks,
Brendan

---

### Post by bjacques123 on 2016-04-06
A few more details...  I'm running Ubuntu 15.04:

```
brendan@brendan-linux:~$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

```

Also, networking on the system does work with a different NIC...  I'm using a USB-ethernet adapter right now.  That led me to think maybe it's a driver issue, so I downloaded the latest from Intel, but that didn't help either:

```
brendan@brendan-linux:~$ modinfo e1000e | grep version
version:        3.3.3-NAPI
srcversion:     BC7D8BD3880A3E5F62C57D7
vermagic:       3.19.0-37-generic SMP mod_unload modversions 

```

---

### Post by gordintoronto on 2016-04-07
Ubuntu 15.04 reached end-of-life a couple of months ago. I suggest you install 15.10, or the beta of 16.04.

---

