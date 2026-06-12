---
title: "Network Card not giving gigabit speeds"
date: 2015-01-31
forum: Networking &amp; Wireless
---

### Post by steveearle86 on 2015-01-31
I have the following setup at home

PC1----switch----switch----switch----PC2

all cabling is cat6 and the switches are gigabit (there are devices attached to each swith, all with cat6)

PC1 is a WIndows 7 PC
PC2 is Ubuntu 14.10 and is used as a file server, sharing two hard disks using Samba.

if I transfer a file from PC to a Samba share in PC2 it transfers at around 12MB/s which to me is more like megabit ethernet speed than gigabit.

I have done the following troubleshoooting

Swapped out PC2 for PC3 which is also a Windows 7 PC which means that the set up was 

PC1----switch----switch----switch----PC3

I then transferred the same file from PC1 to PC3 and the file transfer speed was about 35MB/s which is more like the speeds I am used to on gigabit. This means that there is nothing wrong with the cabling or the switches and the problem lies with PC3.

My next thoughts were that it was an issue with the network card in PC3. As I dont' have a spare NIC, I put the hard drive from PC2 into PC3 and unplugged the Ubuntu boot drive from PC3. This would test whether there was anything wrong with the hardware of PC3(as I already know that the Windows config on that setup works at gigabit from the previous test.

Again, transferring from PC1 to to the PC3 box (with the Windows installation running) was tranferring the file at around 35MB/s which means that there is nothing wrong with the hardware in PC3's box.

This leads me to believe there is some compatibility issue with the NIC on PC3 and Ubuntu. The NIC is the onboard Realtek RTL8111B on the motherboard which is a Gigabyte GA-G33M-DS2R

```
lspci -nnk | grep -iA2 net
``` confirms this

```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168


```

```
ethtool eth0
```  suggests the card is running at gigabit speed

```
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes


```

Any ideas what the issue could be?

---

### Post by steveearle86 on 2015-03-02
I have managed to fix this and it wasn't the issue I thought it was.

My server PC running Ubuntu (PC2) has two disks installed, each of which are set up as samba shares. On my windows PC (PC1) I have both of these Samba Shares mapped as network drives Y:// and Z://

I noticed copying files from Z:// to Y:// in Windows was only transferring the files at 8.50MB/s but when carrying out the same transfer directly on the server PC was doing this at around 30MB/s. This was also the case when I tried on another ubuntu machine transferring them between Samba shares.

This meant it was actually an issue with Samba itself. I added the following to the  [global] section of my smb.conf which has now solved the issue

```
max protocol = SMB2
max xmit = 65535
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=65535 SO_RCVBUF=65535
write raw = yes
read raw = yes
max connections = 65535
max open files = 65335
```

---

