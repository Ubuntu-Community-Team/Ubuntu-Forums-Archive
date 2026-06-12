---
title: "problem with link aggregation / bonding"
date: 2023-04-14
forum: Networking &amp; Wireless
---

### Post by mircot80 on 2023-04-14
HI
I have a problem with link aggregation / bonding.
I have 2 PCs running Ubuntu 22.02.2 LTS connected to the same Zyxel switch with 4 network cables each, I configured the ports in the switch with LAG LACP.
The failover works, I can detach and reattach cables and the connection doesn't drop the problem is that I don't get over 1Gbit data transfer speed with rsync. I also tested with iperf3 but it doesn't exceed 1Gbit (125MB/s).
 
This is my configuration:
 
```
# /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
    eno2:
      dhcp4: false
      dhcp6: false
    eno3:
      dhcp4: false
      dhcp6: false
    eno4:
      dhcp4: false
      dhcp6: false
  bonds:
    bond0:
      interfaces: [eno1, eno2, eno3, eno4]
      addresses:
        - 192.168.69.241/24
      routes:
        - to: default
          via: 192.168.69.1
      parameters:
        mode: 802.3ad
        lacp-rate: fast
        transmit-hash-policy: layer2+3
        mii-monitor-interval: 1
      nameservers:
        addresses:
          - "192.168.69.1"
          - "8.8.8.8"
```
 
 
cat /proc/net/bonding/bond0

```
Ethernet Channel Bonding Driver: v5.19.0-38-generic
 
Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2+3 (2)
MII Status: up
MII Polling Interval (ms): 1
Up Delay (ms): 0
Down Delay (ms): 0
Peer Notification Delay (ms): 0
 
802.3ad info
LACP active: on
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
 
Slave Interface: eno1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 2
Permanent HW addr: 70:10:6f:b1:d5:48
Slave queue ID: 0
Aggregator ID: 3
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 1
Partner Churned Count: 1
 
Slave Interface: eno2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 1
Permanent HW addr: 70:10:6f:b1:d5:49
Slave queue ID: 0
Aggregator ID: 3
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 1
Partner Churned Count: 1
 
Slave Interface: eno3
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 1
Permanent HW addr: 70:10:6f:b1:d5:4a
Slave queue ID: 0
Aggregator ID: 3
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 1
Partner Churned Count: 1
 
Slave Interface: eno4
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 1
Permanent HW addr: 70:10:6f:b1:d5:4b
Slave queue ID: 0
Aggregator ID: 3
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 0
Partner Churned Count: 1

``` 

sudo ethtool bond0

```
Settings for bond0:
                Supported ports: [  ]
                Supported link modes:   Not reported
                Supported pause frame use: No
                Supports auto-negotiation: No
                Supported FEC modes: Not reported
                Advertised link modes:  Not reported
                Advertised pause frame use: No
                Advertised auto-negotiation: No
                Advertised FEC modes: Not reported
                Speed: 4000Mb/s
                Duplex: Full
                Auto-negotiation: off
                Port: Other
                PHYAD: 0
                Transceiver: internal
                Link detected: yes

``` 

Ifconfig

```
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
        inet 192.168.69.241  netmask 255.255.255.0  broadcast 192.168.69.255
        inet6 fe80::b46e:25ff:fe9c:8abf  prefixlen 64  scopeid 0x20<link>
        ether b6:6e:25:9c:8a:bf  txqueuelen 1000  (Ethernet)
        RX packets 61072689  bytes 6976302210 (6.9 GB)
        RX errors 0  dropped 151  overruns 0  frame 0
        TX packets 798124863  bytes 1210130719258 (1.2 TB)
        TX errors 0  dropped 84 overruns 0  carrier 0  collisions 0
 
eno1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether b6:6e:25:9c:8a:bf  txqueuelen 1000  (Ethernet)
        RX packets 5564364  bytes 486714018 (486.7 MB)
        RX errors 0  dropped 13  overruns 0  frame 0
        TX packets 1986590550  bytes 3013796845181 (3.0 TB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16 
 
eno2: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether b6:6e:25:9c:8a:bf  txqueuelen 1000  (Ethernet)
        RX packets 5034526  bytes 391017649 (391.0 MB)
        RX errors 0  dropped 11  overruns 0  frame 0
        TX packets 60487971  bytes 91704277506 (91.7 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17 
 
eno3: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether b6:6e:25:9c:8a:bf  txqueuelen 1000  (Ethernet)
        RX packets 282869  bytes 25905434 (25.9 MB)
        RX errors 0  dropped 9  overruns 0  frame 0
        TX packets 2718224  bytes 4044623091 (4.0 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16 
 
eno4: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether b6:6e:25:9c:8a:bf  txqueuelen 1000  (Ethernet)
        RX packets 141375194  bytes 13045655688 (13.0 GB)
        RX errors 0  dropped 143  overruns 0  frame 0
        TX packets 75382626  bytes 114260610339 (114.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17 
 
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1901886  bytes 779196787 (779.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1901886  bytes 779196787 (779.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

``` 

Where am I wrong?

---

### Post by TheFu on 2023-04-14
Does your switch support it? Cheap switched usually do not.

---

### Post by mircot80 on 2023-04-15
Yes, it is a Zyxel GS1920-24 managed in Nebula cloud

---

### Post by mircot80 on 2023-04-16
I noticed that if I start a file copy to PC1 from PC2 the speed is 1Gbit but if at the same time I start a file copy to PC1 from PC3 the speed is always 1Gbit, PC1 is receiving data at a total speed of 2Gbit.
It seems that the bond works but that a pc can't use more than one network port, is it possible?

---

### Post by TheFu on 2023-04-16
In general, NICs are single threaded for xfers, so the top speed would be 1 Gbps (920Mbps without any file transfer protocol overhead).  Generally, storage performance will limit speed unless you have NVMe SSDs on both sides.

If you use a protocol that supports multiple threads, then those threads would be assigned to different NICs in the bond and you can get higher performance.  For example, NFSv4 has a "nconnect" option which will allow multiple channels to be used. ```


# Create file list:
$ find /source -type f > files.txt
# multiprocess copy:
$ parallel -a files.txt rsync -a {} /dest
```

Someone using this method reported a copy that tool 2 minutes was reduced to 9 seconds. He said nothing about storage or network capacity, so the best we should hope for is that it was faster.

---

### Post by mircot80 on 2023-04-17
is using parallel the same as running 2 rsync at the same time?

---

### Post by mircot80 on 2023-04-17
nothing to do, I do not exceed 118MB/s

---

### Post by TheFu on 2023-04-18
> **mircot80 said:**
> is using parallel the same as running 2 rsync at the same time?

The manpage explains:
```
NAME
       parallel - build and execute shell command lines from standard input in
       parallel
...
DESCRIPTION
       GNU parallel is a shell tool for executing jobs in parallel using one or more
       computers. A job can be a single command or a small script that has to be run
       for each of the lines in the input. The typical input is a list of files, a
       list of hosts, a list of users, a list of URLs, or a list of tables. A job can
       also be a command that reads from a pipe. GNU parallel can then split the
       input into blocks and pipe a block into each command in parallel.

       If you use xargs and tee today you will find GNU parallel very easy to use as
       GNU parallel is written to have the same options as xargs. If you write loops
       in shell, you will find GNU parallel may be able to replace most of the loops
       and make them run faster by running several jobs in parallel.

   Reader's guide
       Start by watching the intro videos for a quick introduction:
       http://www.youtube.com/playlist?list=PL284C9FF2488BC6D1

       Then look at the EXAMPLEs after the list of OPTIONS. That will give you an
       idea of what GNU parallel is capable of.

```
The EXAMPLE section is very useful and has explanations for each of the many examples provided.

---

### Post by mircot80 on 2023-04-18
I tried yesterday but the maximum speed does not change

---

### Post by TheFu on 2023-04-18
> **mircot80 said:**
> I tried yesterday but the maximum speed does not change

Storage performance matters too.  100 MBps storage is pretty standard for spinning disks connected via SATA.  There are faster and slower storage subsystems.

But only you know what's happening. There's no magic bullet. Sorry.

---

### Post by mircot80 on 2023-04-20
if I copy at the same time from 2 pc to pc1 on 2 different hard disks I reach a speed of 2Gbit/sec.
If I copy 2 files from 2 hard disks from a pc to pc1 on 2 different hard disks, I do not exceed the speed of 1Gbit/sec.
It's not a storage problem.
Anyway today I ordered 2 10Gbit fiber network cards...

---

### Post by TheFu on 2023-04-20
If you don't show the commands, we can't see "how" you are doing the copies.  It matters.
2 different PCs are definitely using 2 different processes, each would hit the 1Gbps (probably more like 920 Mbps after protocol overhead), but use 2 different interfaces. 2 Gbps total.
1 PC copying 2 files could be using 1 process and a single NIC, which would be limited to 1 Gbps.

When I copy files using NFS with 2 connections, I'm seeing about 32MB/s ... 256 Mbps on a slower source disk (WD-RED) 
and 
about the same on a WD-Black HDD.  The target disk is the same - a "WD-Blue".
Going in the opposite direction, using rsync+ssh to an NVMe, I'm seeing, 45MBps (350Mbps). NFS isn't using any encryption.  rsync uses ssh by default, which is the only way I have it setup.

Another test ... SATA SSD source ---> NVMe SSD Target ... 44MBps.  **Looks like ssh it where my overhead comes in.**

So, to remove ssh and encryption overhead, I dropped a 3.2G file onto an internal web server here running off an SSD. Then used wget to grab the file.  Saw 112MB/s (896 Mbps) for a single transfer.
When I did 2 transfers from clients, the throughput was split ... 47.3 MB/s and 48.3 MB/s (95.6MB/s total).
If I had 2 bonded interfaces, I'd expect both of those transfers to be 112MB/s ... thanks to disk caching.

10Gbps network stuff is cheap enough for small businesses and home enthusiasts.  I was an early adopter for Gbps networking at home. If you need the speed, it is a cheap upgrade, though in a house, I probably wouldn't get fibre unless the house was pre-wired for it.

---

