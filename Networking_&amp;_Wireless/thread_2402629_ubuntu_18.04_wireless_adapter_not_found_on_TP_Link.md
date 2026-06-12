---
title: "ubuntu 18.04 wireless adapter not found on TP Link Archer T4U"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by rckmtsn on 2018-10-02
Hi,

Every time I get a system update.  Sometimes my wireless adapter doesn't work.  It is a TP Link Archer T4U.  I've tried other things but still not working here is the lshw -c network:  

 root@rick-System-Product-Name:~# lshw -c network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 20:cf:30:5e:70:22
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.62 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febf0000-febfffff


and the ifconfig:

# ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.62  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::22cf:30ff:fe5e:7022  prefixlen 64  scopeid 0x20<link>
        ether 20:cf:30:5e:70:22  txqueuelen 1000  (Ethernet)
        RX packets 24506  bytes 20891292 (20.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18940  bytes 2704797 (2.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3631  bytes 318587 (318.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3631  bytes 318587 (318.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

if anything else you need please tell me.

Thank you in advance.

---

### Post by chili555 on 2018-10-02
Please run and post: ```
lsusb 
``` Thanks.

---

### Post by rckmtsn on 2018-10-02
and the iw config:

# iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

lsusb is:

# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2357:0101  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2357:0101  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2018-10-02
With a temporary working internet connection, open a terminal and do:```
sudo apt update
sudo apt install rtl8812au-dkms
```Reboot and enjoy!

---

### Post by rckmtsn on 2018-10-02
You're the man thank you sir.  Is there a fix for this or will it be coming out soon?

---

### Post by chili555 on 2018-10-02
> **rckmtsn said:**
> You're the man thank you sir.  Is there a fix for this or will it be coming out soon?Errrmm, I think you just applied the fix. I assume that the correct driver rtl8812au will make it into the mainstream kernel at some early point. In the meantime, the dkms process will rebuild the driver for you automagically every time Update Manager offers a later kernel version.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by Randy_Bass on 2019-01-22
> **chili555 said:**
> With a temporary working internet connection, open a terminal and do:```
sudo apt update
sudo apt install rtl8812au-dkms
```Reboot and enjoy!


This is what worked for me. I could not get the original build files to compile without errors since upgrading to 18.04, but I'm up and running again with this. Luckily, I have and old wifi router in bridge mode connected to my wired NIC for backup.

---

