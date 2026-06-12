---
title: "Slow gigbit nic"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by Michael_McKenney on 2014-10-01
Tyan Thunder K8WE Server board
Dual AMD 280 Opterons
4GB RAM

Two nics each use Nvidia NForce Pro 2050 and 2200 chipsets.   

This workstation had XP Pro x64 and Symantec Backup Exec 
Adaptec 29320 SCSI controller
HP LTO 3 tape drive
Two Exabyte VXA-2 tape drives

My previous backups took 2.5 hours to complete in Backup Exec.  Bacula ran for 5+ hours.  

```

[2:0:0:0]    cd/dvd  TSSTcorp CDDVDW SH-S223Q  SB00  /dev/sr0 
[4:0:0:0]    disk    ATA      ST3500320AS      SD15  /dev/sda 
[5:0:0:0]    disk    ATA      ST3500320AS      SD15  /dev/sdb 
[6:0:10:0]   tape    EXABYTE  VXA-3            3233  /dev/st0 
[6:0:12:0]   tape    EXABYTE  VXA-3            3233  /dev/st1 
[7:0:13:0]   tape    HP       Ultrium 3-SCSI   D22D  /dev/st2 
root@Tape:/home/michael# 

root@Tape:/home/michael# lspci
00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev a3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600 LE] (rev a2)
10:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X Bridge (rev 12)
10:0a.1 PIC: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
10:0b.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X Bridge (rev 12)
10:0b.1 PIC: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
11:04.0 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)
11:04.1 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)
80:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
80:01.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
80:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev a3)
80:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
root@Tape:/home/michael# 

root@Tape:/home/michael# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:81:70:18:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:e0:81:70:18:0f  
          inet addr:192.168.0.66  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe70:180f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4203957 (4.2 MB)  TX bytes:488293 (488.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126272 (126.2 KB)  TX bytes:126272 (126.2 KB)

root@Tape:/home/michael# 

oot@Tape:/home/michael# ethtool eth1
Settings for eth1:
    Supported ports: [ MII ]
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
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes
root@Tape:/home/michael# ^C



```

```

michael@Tape:~$ sudo su
[sudo] password for michael: 
root@Tape:/home/michael# cat /proc/sys/net/ipv4/tcp_mem
92790    123720    185580
root@Tape:/home/michael# cat /proc/sys/net/core/rmem_default
212992
root@Tape:/home/michael# cat /proc/sys/net/core/rmem_max
212992
root@Tape:/home/michael# cat /proc/sys/net/core/wmem_default
212992
root@Tape:/home/michael# cat /proc/sys/net/core/wmem_max
212992
root@Tape:/home/michael# cat /proc/sys/net/core/optmem_max
20480
root@Tape:/home/michael# sudo gedit /etc/sysctl.conf


```

```

I have not modified /etc/sysctl.conf

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#


```

---

### Post by tgalati4 on 2014-10-01
If you have any symbolic links in your home directory, then they will get backed up as well.  Simple things like a music share or a network file share in your home directory will get backed up.  Those networked links can take a long, long time.  

You can use *iperf* to test the speed of your network cards to make sure they are working correctly.  How big is the dataset that you backed up in Windows vs Linux?

Exactly how are you backing up?  Are you simply writing tar files to tape?  [Bacula]("https://help.ubuntu.com/community/Bacula") is available in Windows.  Try running Bacula in Windows to compare speed.  I'm sure the Symantic Backup Exec product is pretty well optimized for speed.  It has been around a long time.

---

### Post by Michael_McKenney on 2014-10-01
Three tape devices:
HP LTO 3 :  Ubuntu web server : 150GB
VXA-2 10:  Tape local box
VXA-2 12:  Windows 7 x64 Ultimate

Symantec would do 1630, 680, and 630 MB/min on concurrent jobs.  I had 512 MB read/write buffers configured.

---

### Post by Michael_McKenney on 2014-10-01
I installed a Intel PCIe x1 NIC to see if it performed better.  

Test 1:  Ubuntu web server client to Tape server

```

root@Tape:/home/michael# iperf -s 
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.66 port 5001 connected with 192.168.0.48 port 48357
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   610 MBytes   510 Mbits/sec
[  5] local 192.168.0.66 port 5001 connected with 192.168.0.48 port 48358
[  5]  0.0-20.0 sec  1.19 GBytes   510 Mbits/sec

test #2  Tape client to Ubuntu server
root@Tape:/home/michael# iperf -c 192.168.0.48 -t 20
------------------------------------------------------------
Client connecting to 192.168.0.48, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.66 port 48945 connected with 192.168.0.48 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-20.0 sec  1.42 GBytes   608 Mbits/sec
root@Tape:/home/michael# iperf -c 192.168.0.48 -t 80
------------------------------------------------------------
Client connecting to 192.168.0.48, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.66 port 48946 connected with 192.168.0.48 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-80.0 sec  5.65 GBytes   607 Mbits/sec
root@Tape:/home/michael# 






```

---

### Post by Michael_McKenney on 2014-10-01
Reran the test
```

root@Tape:/home/michael# cat /proc/sys/net/ipv4/tcp_mem
92790    123720    185580
root@Tape:/home/michael# cat /proc/sys/net/core/rmem_default
212992
root@Tape:/home/michael# cat /proc/sys/net/core/rmem_max
212992
root@Tape:/home/michael# cat /proc/sys/net/core/wmem_default
212992
root@Tape:/home/michael# cat /proc/sys/net/core/wmem_max
212992
root@Tape:/home/michael# cat /proc/sys/net/core/optmem_max
20480



```

---

### Post by tgalati4 on 2014-10-01
The fact that you can't get over 900 Mbits/sec on a gigabit network means you either have a cabling problem,  or a switch problem, or a traffic problem.  Your sustained rates of 608 Mbits/sec means that you are getting 76 MBytes/sec, or about the same speed as an older IDE, desktop hard disk (such as a WD Raptor).  That works out to 4.56 GB per min.  So I doubt that your NIC's are the bottleneck in this situation.

---

### Post by Michael_McKenney on 2014-10-01
Cables are CAT 6.  The switch is a Dlink DGS-2205.   The hard drives are single drives not RAID.

Tape:  ST3500320AS 500GB SATA 3 Gbps  7200.11
Ubuntu Web Site: ST3500630A ATA

I have another SATA ST3500320AS drive that can go into Ubuntu.   However, the backup speed was 1630 MB/min on the tape drives with XP and Symantec.

---

### Post by Michael_McKenney on 2014-10-01
```

 	    [TABLE]
 	 	[TR]
 		[TD="align: right"]1[/TD]
 		[TD="align: left"]hour[/TD]
 		[TD="align: right"]1[/TD]
 	[/TR]
 	[TR]
 		[TD="align: right"]22[/TD]
 		[TD="align: left"]minute[/TD]
 		[TD="align: right"]0.3666666667[/TD]
 	[/TR]
 	[TR]
 		[TD="align: right"]1[/TD]
 		[TD="align: left"]seconds[/TD]
 		[TD="align: right"]0.0002777778[/TD]
 	[/TR]
 	[TR]
 		[TD="align: left"][/TD]
 		[TD="align: left"][/TD]
 		[TD="align: left"][/TD]
 	[/TR]
 	[TR]
 		[TD="align: left"][/TD]
 		[TD="align: left"]Hours[/TD]
 		[TD="align: right"]1.3669444444[/TD]
 	[/TR]
 	[TR]
 		[TD="align: left"][/TD]
 		[TD="align: left"][/TD]
 		[TD="align: left"][/TD]
 	[/TR]
 	[TR]
 		[TD="align: right"]37783.2[/TD]
 		[TD="align: left"]KB/s[/TD]
 		[TD="align: left"][/TD]
 	[/TR]
 	[TR]
 		[TD="align: right"]36.89765625[/TD]
 		[TD="align: left"]MB/s[/TD]
 		[TD="align: left"][/TD]
 	[/TR]
 	[TR]
 		[TD="align: right"]2213.859375[/TD]
 		[TD="align: left"]MB/min[/TD]
 		[TD="align: left"][/TD]
 	[/TR]
 [/TABLE]


01-Oct 19:13 Tape-dir JobId 49: Start Backup JobId 49, Job=HPLTO3_Test.2014-10-01_19.13.12_06
01-Oct 19:13 Tape-dir JobId 49: Using Device "HPLTO3"
01-Oct 19:13 Tape-sd JobId 49: Error: block.c:275 Volume data error at 0:0! Wanted ID: "BB02", got "". Buffer discarded.
01-Oct 19:13 Tape-sd JobId 49: Please mount Volume "File0004" or label a new one for:
    Job:          HPLTO3_Test.2014-10-01_19.13.12_06
    Storage:      "HPLTO3" (/dev/st2)
    Pool:         HPLTO3_4_Full
    Media type:   LTO-3
01-Oct 19:16 Tape-sd JobId 49: Wrote label to prelabeled Volume "File0004" on device "HPLTO3" (/dev/st2)
01-Oct 19:16 Tape-dir JobId 49: Volume used once. Marking Volume "File0004" as Used.
01-Oct 20:30 Tape-sd JobId 49: Job write elapsed time = 01:14:07, Transfer rate = 41.81 M Bytes/second
01-Oct 20:35 Tape-dir JobId 49: Bacula Tape-dir 5.2.6 (21Feb12):
  Build OS:               x86_64-pc-linux-gnu ubuntu 14.04
  JobId:                  49
  Job:                    HPLTO3_Test.2014-10-01_19.13.12_06
  Backup Level:           Full
  Client:                 "ubuntu-fd" 5.2.6 (21Feb12) x86_64-pc-linux-gnu,ubuntu,14.04
  FileSet:                "UbuntuTestSet" 2014-10-01 18:55:02
  Pool:                   "HPLTO3_4_Full" (From Job FullPool override)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "HPLTO3" (From Pool resource)
  Scheduled time:         01-Oct-2014 19:13:12
  Start time:             01-Oct-2014 19:13:30
  End time:               01-Oct-2014 20:35:31
  Elapsed time:           1 hour 22 mins 1 sec
  Priority:               10
  FD Files Written:       58,512
  SD Files Written:       58,512
  FD Bytes Written:       185,931,234,507 (185.9 GB)
  SD Bytes Written:       185,941,350,708 (185.9 GB)
  Rate:                   37783.2 KB/s
  Software Compression:   None
  VSS:                    no
  Encryption:             no
  Accurate:               no
  Volume name(s):         File0004
  Volume Session Id:      1
  Volume Session Time:    1412205180
  Last Volume Bytes:      186,081,122,304 (186.0 GB)
  Non-fatal FD errors:    0
  SD Errors:              1
  FD termination status:  OK
  SD termination status:  OK
  Termination:            Backup OK -- with warnings

01-Oct 20:35 Tape-dir JobId 49: Begin pruning Jobs older than 6 months .
01-Oct 20:35 Tape-dir JobId 49: No Jobs found to prune.
01-Oct 20:35 Tape-dir JobId 49: Begin pruning Files.
01-Oct 20:35 Tape-dir JobId 49: No Files found to prune.
01-Oct 20:35 Tape-dir JobId 49: End auto prune.


```

The new NIC is up to 2213.85 MB/min and 1 hour 22 minutes. So what would increasing the buffers get me?

---

