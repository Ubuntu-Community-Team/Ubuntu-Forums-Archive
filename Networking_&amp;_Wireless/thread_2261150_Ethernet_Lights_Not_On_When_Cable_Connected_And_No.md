---
title: "Ethernet Lights Not On When Cable Connected And Not Working"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by Daniyal_Javani on 2015-01-16
I have two OS and second OS connects to internet easily, so it's not a hardware problem.

The output of lspci is:

    ```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
    00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
    00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
    00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
    00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
    00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
    00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
    00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
    00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
    23:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
    23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
    23:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
    24:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

lshw -C network:
 
 ```
    *-network               
           description: Wireless interface
           product: AR9285 Wireless Network Adapter (PCI-Express)
           vendor: Qualcomm Atheros
           physical id: 0
           bus info: pci@0000:24:00.0
           logical name: wlan0
           version: 01
           serial: 74:de:2b:02:0b:da
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=ath9k driverversion=3.18.2-031802-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
           resources: irq:19 memory:d4600000-d460ffff
      *-network
           description: Ethernet interface
           product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:25:00.0
           logical name: eth0
           version: 06
           serial: 10:1f:74:e3:50:5a
           size: 10Mbit/s
           capacity: 1Gbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.100 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
           resources: irq:29 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff

```
ifup eth0 
```

    Internet Systems Consortium DHCP Client 4.2.4
    Copyright 2004-2012 Internet Systems Consortium.
    All rights reserved.
    For info, please visit https://www.isc.org/software/dhcp/
    
    Listening on LPF/eth0/10:1f:74:e3:50:5a
    Sending on   LPF/eth0/10:1f:74:e3:50:5a
    Sending on   Socket/fallback
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x78a08d03)
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x78a08d03)
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 (xid=0x78a08d03)
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19 (xid=0x78a08d03)
    ...
    (infinite, continue for ever)
```

ifconfig -a

```
    eth0      Link encap:Ethernet  HWaddr 10:1f:74:e3:50:5a  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:298 errors:0 dropped:0 overruns:0 frame:0
              TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:23133 (23.1 KB)  TX bytes:23133 (23.1 KB)
    
    wlan0     Link encap:Ethernet  HWaddr 74:de:2b:02:0b:da  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    vim /etc/network/interfaces
    auto lo
    iface lo inet loopback
    
    auto eth0
    iface eth0 inet dhcp
```

cat /etc/resolv.conf

```
    # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
    nameserver 127.0.1.
```1

route -n

```
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

I'm also try static IP address but still have the problem. Please help me, I really do not have any other idea!

**UPDATE**

When I run ifup eth0, syslog output is
```

    Jan 16 22:42:34 DEMON kernel: [16477.474586] r8169 0000:25:00.0 eth0: link down
    Jan 16 22:42:34 DEMON avahi-daemon[1167]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
    Jan 16 22:42:34 DEMON avahi-daemon[1167]: New relevant interface eth0.IPv4 for mDNS.
    Jan 16 22:42:34 DEMON avahi-daemon[1167]: Registering new address record for 192.168.1.100 on eth0.IPv4.
    Jan 16 22:42:34 DEMON kernel: [16477.475316] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
```

So I try Linux kernel version 14 and 18, but both have same problem.
Any idea?
**UPDATE2**

I try to use static IP adress so change interfaces:
```

    auto lo
    iface lo inet loopback
    
    auto dsl-provider
    iface dsl-provider inet ppp
    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
    dns-nameservers 8.8.8.8 8.8.4.4
    provider dsl-provider
    
    auto eth0
    iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
```

Then ifconfig -a

    ```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:e3:50:5a  
              inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:439 errors:0 dropped:0 overruns:0 frame:0
              TX packets:439 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:34837 (34.8 KB)  TX bytes:34837 (34.8 KB)
    
    ppp0      Link encap:Point-to-Point Protocol  
              inet addr:37.254.165.125  P-t-P:37.254.128.1  Mask:255.255.255.255
              UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
              RX packets:7259 errors:0 dropped:0 overruns:0 frame:0
              TX packets:8600 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:3 
              RX bytes:4900816 (4.9 MB)  TX bytes:1303955 (1.3 MB)
    
    wlan0     Link encap:Ethernet  HWaddr 74:de:2b:02:0b:da  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

sudo ethtool eth0

    ```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  100baseT/Full 
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000033 (51)
                       drv probe ifdown ifup
        Link detected: no

```

---

### Post by praseodym on 2015-01-17
Try to change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u 
```
Reboot. Are you using the network-manager? Or "only"
```

sudo pppoeconf
```

---

