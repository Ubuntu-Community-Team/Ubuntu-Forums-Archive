---
title: "Server 13.10 - Gigabit Ethernet low bandwidth in one direction and RX CRC Errors"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by michal19 on 2015-04-20
Hello everyone!

After few days of "fighting" the problem i decided to post new thread here, since im running out of ideas how to solve it.


[SIZE=4]**Introduction:**[/SIZE]

First, few words about how LAN is designed:

- _Gigabit switch_, every single connected machine is working in 1000Mbits/sec (there are different LED's for different connection speeds, so you can easily check the mode on each connected ethernet cable),

- _Gigabit router QNO QVF7303_, connected to WAN and to LAN via switch mentioned before, working in 1000Mbits/sec, full duplex (negotiation is set to auto on port), DHCP server,

- _Server HP ProLiant DL380G6_, running on _Ubuntu 13.10 Server_, 4 ethernet gigabit ports (using only one of them, working in 1000Mbits/sec), hardware RAID1 on 3x SSD drives (200GB total space) and hardware RAID1 on 3x HDD drives (2TB total space), DHCP configuration,

- _About 30 PC's_, mostly running on Windows 7, some running on different Ubuntu Desktop distros, each machine is using gigabit ethernet card, DHCP configurations,


[SIZE=4]**Problem:**[/SIZE]

**Bandwidth speed** measured in iperf **is really slow** between server (1.210) and any other connected machine, **but ONLY in one direction** - example:

```

root@dev:~# **iperf -s**
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.210 port 5001 connected with 192.168.1.101 port 50280
------------------------------------------------------------
Client connecting to 192.168.1.101, TCP port 5001
TCP window size:  256 KByte (default)
------------------------------------------------------------
[  6] local 192.168.1.210 port 48048 connected with 192.168.1.101 port 5001
[ ID] Interval       Transfer     Bandwidth
[  6]  0.0-10.0 sec  1.03 **GBytes**   885 **Mbits**/sec
[  4]  0.0-13.0 sec  1.25 **MBytes**   806 **Kbits**/sec

```

This is the result after connecting to server (1.210) from my PC (1.101), running on Windows 7.
As you can see, im getting gigabit badwidth from server to my PC, but only ~ 1Mbit's from my PC to server.

Every single file transfer, on every protocol behaves the same (FTP, SCP, Samba) - download from server is fast, upload is horrible (kilobytes / sec).

At this point, it's worth mentioning, that transfers between PC's are fine - here's example of test between my PC (1.101) and different PC running Ubuntu Desktop (1.115):

```

e:\Downloads\**iperf-2.0.5-3-win32>iperf -c 192.168.1.115 -d**
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 63.0 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.115, TCP port 5001
TCP window size: 63.0 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.101 port 51890 connected with 192.168.1.115 port 5001
[  5] local 192.168.1.101 port 5001 connected with 192.168.1.115 port 49302
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   813 MBytes   682 Mbits/sec
[  5]  0.0-10.0 sec   710 MBytes   595 Mbits/sec

```

Another important thing, that indicates that it's most likely not hardware problem is:

_After connecting another PC into the same ethernet cable that server was using_ (same cable, same gigabit switch port - just unplugged cable from server and plugged into different maching), _transfers were fine_ which tells me that cables and switch ports are fine aswell.


[SIZE=4]**Additional informations:**[/SIZE]

Even tho i kind of proved that the problem isn't in cables or switch, i still did the test with connecting different cable to different port on the switch AND different ethernet card on the server (as stated before, server has 4 ethernet cards) - result was the same, which brings me to the point where i started suspecting ethernet drivers.

_Disks_: As stated before, i was using iperf to measure bandwith - here are read / write stats for server disks:

- RAID1 on **SSD **drives (**read**):
```

root@dev:~# **hdparm -Tt /dev/sda**

/dev/sda:
 Timing cached reads:   14014 MB in  2.00 seconds = 7013.13 MB/sec
 Timing buffered disk reads: 1170 MB in  3.00 seconds = 389.45 MB/sec

```

- RAID1 on **HDD **drives (**read**):
```

root@dev:~# **hdparm -Tt /dev/sdb**

/dev/sdb:
 Timing cached reads:   13644 MB in  2.00 seconds = 6827.85 MB/sec
 Timing buffered disk reads: 404 MB in  3.00 seconds = 134.56 MB/sec

```

- RAID on **SSD **drives (**write**):
```

root@dev:/ssd-data# **dd if=/dev/zero of=/ssd-data/output bs=8k count=100k**
102400+0 przeczytanych recordów
102400+0 zapisanych recordów
skopiowane 838860800 bajtów (839 MB), 0,91047 s, 921 MB/s

``` 
(sorry, it's in Polish, but you can still read every value to get the idea)

- RAID on **HDD **drives (**write**):
```

root@dev:/hdd-data# **dd if=/dev/zero of=/hdd-data/output bs=8k count=100k**
102400+0 przeczytanych recordów
102400+0 zapisanych recordów
skopiowane 838860800 bajtów (839 MB), 1,35917 s, 617 MB/s

``` 
(sorry, it's in Polish, but you can still read every value to get the idea)

_Network configuration on server_:

```

root@dev:~# **ifconfig**
br0       Link encap:Ethernet  HWaddr 78:e7:d1:93:4c:64
          inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae7:d1ff:fe93:4c64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41193625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38893466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24792466455 (24.7 GB)  TX bytes:54108139941 (54.1 GB)


em1       Link encap:Ethernet  HWaddr 78:e7:d1:93:4c:64
          inet6 addr: fe80::7ae7:d1ff:fe93:4c64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47977247 errors:**1270942** dropped:0 overruns:0 frame:1270942
          TX packets:59209232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26048933797 (26.0 GB)  TX bytes:55683174510 (55.6 GB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4481631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4481631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2859189532 (2.8 GB)  TX bytes:2859189532 (2.8 GB)


virbr0    Link encap:Ethernet  HWaddr c2:17:6c:3f:29:63
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**Note RX Errors on em1.**

**br0** is the bridge configured for KVM virtual machines usage. _When using only **em1** without bridge, the problem still appears, same as for using **em2** (second ethernet card)._

```

root@dev:~# **cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Secondary network interface
#auto em2
#iface em2 inet dhcp

# The primary network interface
#auto em1
#iface em1 inet dhcp

# Virtual machines bridge
auto br0
iface br0 inet dhcp
  bridge_ports em1
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off

```

```

root@dev:~# **ethtool em1**
Settings for em1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes

```

```

root@dev:~# **ethtool -S em1**
NIC statistics:
     rx_bytes: 26452913865
     rx_error_bytes: 0
     tx_bytes: 55909229390
     tx_error_bytes: 0
     rx_ucast_packets: 48304551
     rx_mcast_packets: 56138
     rx_bcast_packets: 385115
     tx_ucast_packets: 59887576
     tx_mcast_packets: 17
     tx_bcast_packets: 677
     tx_mac_errors: 0
     tx_carrier_errors: 0
**     rx_crc_errors: 1294846**
     rx_align_errors: 0
     tx_single_collisions: 0
     tx_multi_collisions: 0
     tx_deferred: 0
     tx_excess_collisions: 0
     tx_late_collisions: 0
     tx_total_collisions: 0
     rx_fragments: 120
     rx_jabbers: 256287
     rx_undersize_packets: 0
     rx_oversize_packets: 0
     rx_64_byte_packets: 2820562
     rx_65_to_127_byte_packets: 16431986
     rx_128_to_255_byte_packets: 8498512
     rx_256_to_511_byte_packets: 6643494
     rx_512_to_1023_byte_packets: 1471190
     rx_1024_to_1522_byte_packets: 13344528
     rx_1523_to_9022_byte_packets: 0
     tx_64_byte_packets: 177065
     tx_65_to_127_byte_packets: 9532242
     tx_128_to_255_byte_packets: 14312188
     tx_256_to_511_byte_packets: 995217
     tx_512_to_1023_byte_packets: 399221
     tx_1024_to_1522_byte_packets: 34472337
     tx_1523_to_9022_byte_packets: 0
     rx_xon_frames: 70794
     rx_xoff_frames: 393674
     tx_xon_frames: 0
     tx_xoff_frames: 0
     rx_mac_ctrl_frames: 0
     rx_filtered_packets: 466020
     rx_ftq_discards: 0
     rx_discards: 0
     rx_fw_discards: 0

```

```

root@dev:~# **ethtool -a em1**
Pause parameters for em1:
Autonegotiate:  on
RX:             on
TX:             on

```

```

root@dev:~# **ethtool -i em1**
driver: bnx2
version: 2.2.3
firmware-version: bc 4.6.4 NCSI 1.0.3
bus-info: 0000:02:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

```

```

root@dev:~# **dmesg | grep -i duplex**
[    6.984481] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex

```

```

root@dev:~# **lspci**
00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:04.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 4 (rev 13)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13)
00:06.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 6 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:08.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 8 (rev 13)
00:09.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:0a.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 10 (rev 13)
00:0d.0 Host bridge: Intel Corporation Device 343a (rev 13)
00:0d.1 Host bridge: Intel Corporation Device 343b (rev 13)
00:0d.2 Host bridge: Intel Corporation Device 343c (rev 13)
00:0d.3 Host bridge: Intel Corporation Device 343d (rev 13)
00:0d.4 Host bridge: Intel Corporation 7500/5520/5500/X58 Physical Layer Port 0 (rev 13)
00:0d.5 Host bridge: Intel Corporation 7500/5520/5500 Physical Layer Port 1 (rev 13)
00:0d.6 Host bridge: Intel Corporation Device 341a (rev 13)
00:0e.0 Host bridge: Intel Corporation Device 341c (rev 13)
00:0e.1 Host bridge: Intel Corporation Device 341d (rev 13)
00:0e.2 Host bridge: Intel Corporation Device 341e (rev 13)
00:0e.3 Host bridge: Intel Corporation Device 341f (rev 13)
00:0e.4 Host bridge: Intel Corporation Device 3439 (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.3 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
01:03.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] ES1000 (rev 02)
01:04.0 System peripheral: Compaq Computer Corporation Integrated Lights Out Controller (rev 03)
01:04.2 System peripheral: Compaq Computer Corporation Integrated Lights Out  Processor (rev 03)
01:04.4 USB controller: Hewlett-Packard Company Integrated Lights-Out Standard Virtual USB Controller
01:04.6 IPMI SMIC interface: Hewlett-Packard Company Integrated Lights-Out Standard KCS Interface
**02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)**
**02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)**
**03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)**
**03:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)**
04:00.0 RAID bus controller: Hewlett-Packard Company Smart Array G6 controllers (rev 01)
3e:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
3e:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
3e:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
3e:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
3e:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
3e:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
3e:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
3e:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
3e:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
3e:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
3e:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
3e:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
3e:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
3e:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
3e:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
3e:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
3e:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
3e:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
3e:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
3e:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
3e:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
3e:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
3e:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
3e:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)
3f:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
3f:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
3f:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
3f:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
3f:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
3f:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
3f:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
3f:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
3f:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
3f:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
3f:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
3f:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
3f:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
3f:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
3f:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
3f:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
3f:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
3f:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
3f:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
3f:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)

```

```

root@dev:~# **lspci -v**

[...]

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
        Subsystem: Hewlett-Packard Company NC382i Integrated Multi-port PCI Express Gigabit Server Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        [virtual] Expansion ROM at e7100000 [disabled] [size=64K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
        Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
        Capabilities: [ac] Express Endpoint, MSI 00
        Capabilities: [100] Device Serial Number 78-e7-d1-ff-fe-93-4c-64
        Capabilities: [110] Advanced Error Reporting
        Capabilities: [150] Power Budgeting <?>
        Capabilities: [160] Virtual Channel
        Kernel driver in use: bnx2

[...]


```

_What else i have tried_:

- Different configurations of RX, TX, auto-negotiation, MSI support, overload (modified with ethtool) - no results.

- Changing everything to 100Mbits/s - transfer to server still at ~1Mbits/sec.

- Disconnecting router from WAN, removing all unessessary "ip route" commands from routing on the server - no result.

- Monitoring network flow and CPU - LAN isn't overloaded at all (also, did every mentioned test after work, then every PC exept of mine was turned off) - no results.

- Turning off all unnessesary services (including Samba and every service that has to do anything with constant disk / bandwidth usage) - no result.


[SIZE=4]**Conclusion:**[/SIZE]

As i said at the beginning, i ran out of options.

It doesnt seems like the problem with cables or any other network device - everything tells me, there's something wrong with drivers for these Broadcom NIC's, but i decided not to touch them before i get second opinion on that's going on in my LAN... and that's why im writing this post.


_So, the question is_[B]:

Is there anything else i can do to diagnose the source of the problem and get rid of it?
[/B]

Feel free to ask for any more logs / command outputs - i'll deliver them ASAP.

Thank You in advance!

---

### Post by TheFu on 2015-04-20
Support for 13.10 ended last year - June-ish. [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
If you need longer support than 6-9 months from a release, please use LTS releases.

The recommendation would be to migrate to a supported LTS release and see if that solves the issue. 14.04 is what I'd use today.
Searching found this issue with that card: [http://monolight.cc/2011/08/flow-control-flaw-in-broadcom-bcm5709-nics-and-bcm56xxx-switches/](http://monolight.cc/2011/08/flow-control-flaw-in-broadcom-bcm5709-nics-and-bcm56xxx-switches/)

---

### Post by bapoumba on 2015-04-20
Not directly addressing your issues, but 13.10 has reached end of life last July, any reason you are still using an unsupported release ?

---

### Post by michal19 on 2015-04-20
To be honest, i wasnt doing distribution upgrade, cause i didnt want to end up having everything misconfigured in the end, but i was manually taking care of every service to stay in it's highest possible stable version.

So now i assume i wont be able to get any help here until i upgrade?
If that's the case, ill backup everything and will upgrade to 14.14.

---

### Post by TheFu on 2015-04-20
14.04 is what you want. Supported into 2019.
NOT 14.10 - which only has support until June-ish.

Forum policy is to help only with currently supported releases. :|

---

### Post by michal19 on 2015-04-20
Okays, i understand that.

First im gonna look into that link You provided in your previous answer and then im doing dist-upgrade this evening.

Will let You know how it went, thanks.

---

### Post by The Cog on 2015-04-20
I would definitely check the duplex setting of the switch port that connects to the server. All your errors are frame checksum errors, and that many generally indicates a duplex mismatch rather than a poor cable (which you have already eliminated).

If you can't get teh switch to tell you the duplex mode on that port, try setting the server to half duplex and see if that cleans things up.

---

