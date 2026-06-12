---
title: "Slow transfer speed over Gigabit Ethernet"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by Sandesh_Giri on 2015-07-14
I am getting slow transfer speed(less than 30Mbits/s) over my Gigabit Ethernet (built in).  This is basically happening when I am trying to transfer data between my WD My Cloud 2TB over NFS. If I try the same thing on my Windows 8 Laptop (Lenovo Y510P) I get speed upto 250 Mbits/s.

```
Laptop - HP Elitebook 8460P 
Ubuntu - Ubuntu 15.04 x86_64
NIC - Integrated Intel 82579LM Gigabit* Network Connection (vPro configurations)
Ethernet Cable - [FONT=Arial]UTP Cat6
[/FONT]Router - Cisco EPC3928
Driver used - e1000e
Internet Speed - 120 Mbits/s (Ziggo NL)
```


Network Adapter in Ubuntu machine -

```
sandesh@ubuntu:~$ ethtool eth0Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: off (auto)
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes

```

Network Adapter in WD MyCloud 

```

Sandy-WDCloud:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: external
    Auto-negotiation: on
    Current message level: 0x00000036 (54)
                   probe link ifdown ifup
    Link detected: yes

```

After NFS drive mounted.

```

sandesh@ubuntu:~$ df -h
Filesystem                  Size  Used Avail Use% Mounted on
udev                        7,6G     0  7,6G   0% /dev
tmpfs                       1,6G  9,5M  1,6G   1% /run
/dev/sda1                   131G   11G  114G   9% /
tmpfs                       7,6G   20M  7,6G   1% /dev/shm
tmpfs                       5,0M  4,0K  5,0M   1% /run/lock
tmpfs                       7,6G     0  7,6G   0% /sys/fs/cgroup
cgmfs                       100K     0  100K   0% /run/cgmanager/fs
tmpfs                       1,6G   48K  1,6G   1% /run/user/1000
192.168.178.15:/nfs/Oracle  1,8T  149G  1,7T   9% /sandy-wdcloud

```

Copy test to see the actual speed.

```

sandesh@ubuntu:/sandy-wdcloud/operating_systems$ cp ubuntu-15.04-desktop-amd64.iso $HOME/Downloads

```

Screenshots attached.





I have tried to use iperf and made Widows 8 laptop Server and Ubuntu laptop as Client and speed test shows resulting speed upto 900Mbits/s. This is not only happening on Ubuntu but also on other Linux distros I have tried Fedora 22.

---

### Post by Sandesh_Giri on 2015-07-14
Hello Guys,

Any help with this issue or pointers would be appreciated!!!

---

