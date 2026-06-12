---
title: "Verizon FIOS and Ubuntu tweaking"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by guyvertoon on 2007-12-14
Hey All,

     I got Verizon FIOS and love it. However, my speed tests (both Verizons and others) showed me getting less than a third of the speed I am paying for. After searching around for awhile, I stumbled upon this post which worked beautifully. I am now getting full bandwidth as advertised.

[http://www.speedguide.net/read_articles.php?id=121](http://www.speedguide.net/read_articles.php?id=121)

I thought I'd include my /etc/sysctl.conf file contents as well:

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_window_scaling = 1

After editing the file and adding the above, I entered the command sudo sysctl -p to apply the changes and poof, speeds where they should have been :-)

---

### Post by ahfu on 2007-12-25
Hi there,

First time using Linux so do pardon me if I am asking silly questions.
So, to increase speed for my internet, do i simply edit my/etc/sysctl.conf file to having the same contents as yours?

Or do i have to read and apply what is taught in [http://www.speedguide.net/read_articles.php?id=121](http://www.speedguide.net/read_articles.php?id=121)

Thanks!

Ah Fu

---

### Post by guyvertoon on 2007-12-26
LOL, I am checking out Linux Mint and just cut and pasted my own post into the file and rebooted and poof, full speed :-)

---

### Post by 81wtbvi02 on 2007-12-28
It would clear things up for everybody if you would just post the additions you made to your /etc/sysctl.conf file, and not the whole file.

Thank You.

---

### Post by guyvertoon on 2007-12-29
My additions are everything after the last commented line (the one with the # before it). The rest of the file should be pretty consistent regardless of the distro. Also, most would rather see the whole file, unless it is unusually large, makes it easier to compare. ;-)

---

### Post by FoxOne on 2008-01-03
speeds are up just a bit on my DSL after adding the lines to my system, thanks

---

### Post by K_Diegs on 2008-02-09
I have FIOS 20/5 service and I achieve pretty close to the stated service on LINUX no tweaks using Speakeasy.net/speedtest..    However, I am now using the Network Diagnostic Testers (NDT's) for my speed testing.    [http://web100.rit.edu:7123/](http://web100.rit.edu:7123/)       See test results end of this post.

No tweaks to my 6.04 Ubuntu install on a Old 1ghz Tbird Abit KT7A100 ..   Old machine,,  Had her since 1999.   Been rebuilt several times with new hard drives over the years. See test results below on this old tbird.  I  also run a new Dell 530n with 7.04 and my results are very much the same....   E2160 with 3 gig DDR2 667.  Again no tweaks to my TCP/ip or RWIN....    

My Winblowz XP Machines in the house do not get even close to that bandwidth with out running TCPIPoptimizer.   Even then my TBird which is a dual boot to XP, the XP side  isn't quite up to snuff with Ubuntu 6.04.

The only machines on my network that I can't get the bandwidth up to snuff are the machines under a 1ghz processor.   Athalon 850 with XP I get about 2.68Mb/s up and 9.84 Mb/s down...   A PIII550 and I get just under 2 up and 3.8 down.....   

Test Results from [http://web100.rit.edu:7123/](http://web100.rit.edu:7123/)  on my old TBird
WEB100 Enabled Statistics:
Checking for Middleboxes . . . . . . . . . . . . . . . . . .  Done
checking for firewalls . . . . . . . . . . . . . . . . . . .  Done
running 10s outbound test (client-to-server [C2S]) . . . . . 4.56Mb/s
running 10s inbound test (server-to-client [S2C]) . . . . . . 19.45Mb/s

	------  Client System Details  ------
OS data: Name = Linux, Architecture = i386, Version = 2.6.12-10-k7
Java data: Vendor = Sun Microsystems Inc., Version = 1.5.0_05

	------  Web100 Detailed Analysis  ------
Interprocess communications failed, unknown link type.
Link set to Full Duplex mode
No network congestion discovered.
Good network cable(s) found
Normal duplex operation found.

Web100 reports the Round trip time = 50.62 msec; the Packet size = 1448 Bytes; and 
No packet loss - but packets arrived out-of-order 0.13% of the time
C2S throughput test: Packet queuing detected: 1.14%
S2C throughput test: Packet queuing detected: 39.44%
This connection is receiver limited 95.39% of the time.
This connection is sender limited 2.46% of the time.
This connection is network limited 2.15% of the time.

Web100 reports TCP negotiated the optional Performance Settings to: 
RFC 2018 Selective Acknowledgment: ON
RFC 896 Nagle Algorithm: ON
RFC 3168 Explicit Congestion Notification: OFF
RFC 1323 Time Stamping: ON
RFC 1323 Window Scaling: ON

Server 'web100.rit.edu' is not behind a firewall. [Connection to the ephemeral port was successful]
Client is probably behind a firewall. [Connection to the ephemeral port failed]
Information: Network Middlebox is modifying MSS variable
Server IP addresses are preserved End-to-End
Information: Network Address Translation (NAT) box is modifying the Client's IP address

WEB100 Kernel Variables:
Client: alex/127.0.0.1
CurMSS: 1448
X_Rcvbuf: 33554432
X_Sndbuf: 33554432
AckPktsIn: 8565
AckPktsOut: 0
BytesRetrans: 0
CongAvoid: 0
CongestionOverCount: 0
CongestionSignals: 0
CountRTT: 8486
CurCwnd: 125976
CurRTO: 252
CurRwinRcvd: 124528
CurRwinSent: 6144
CurSsthresh: 2147483647
DSACKDups: 0
DataBytesIn: 0
DataBytesOut: 25726840
DataPktsIn: 0
DataPktsOut: 17383
DupAcksIn: 11
ECNEnabled: 0
FastRetran: 0
MaxCwnd: 125976
MaxMSS: 1448
MaxRTO: 256
MaxRTT: 64
MaxRwinRcvd: 124528
MaxRwinSent: 6144
MaxSsthresh: 0
MinMSS: 1428
MinRTO: 236
MinRTT: 32
MinRwinRcvd: 5840
MinRwinSent: 5792
NagleEnabled: 1
OtherReductions: 0
PktsIn: 8565
PktsOut: 17383
PktsRetrans: 0
RcvWinScale: 10
SACKEnabled: 3
SACKsRcvd: 15
SendStall: 0
SlowStart: 84
SampleRTT: 52
SmoothedRTT: 52
SndWinScale: 2
SndLimTimeRwin: 10141604
SndLimTimeCwnd: 228184
SndLimTimeSender: 262060
SndLimTransRwin: 2
SndLimTransCwnd: 2
SndLimTransSender: 1
SndLimBytesRwin: 25416040
SndLimBytesCwnd: 306360
SndLimBytesSender: 4440
SubsequentTimeouts: 0
SumRTT: 429580
Timeouts: 0
TimestampsEnabled: 1
WinScaleRcvd: 2
WinScaleSent: 10
DupAcksOut: 0
StartTimeUsec: 652594
Duration: 10632023
c2sData: -1
c2sAck: -1
s2cData: -1
s2cAck: -1
half_duplex: 0
link: 100
congestion: 0
bad_cable: 0
mismatch: 0
spd: 19.36
bw: 218.23
loss: 0.000001000
avgrtt: 50.62
waitsec: 0.00
timesec: 10.00
order: 0.0013
rwintime: 0.9539
sendtime: 0.0246
cwndtime: 0.0215
rwin: 0.9501
swin: 256.0000
cwin: 0.9611
rttsec: 0.050622
Sndbuf: 33554432
aspd: 0.00000
CWND-Limited: 651.88

The theoretical network limit is 218.23 Mbps
The NDT server has a 16384.0 KByte buffer which limits the throughput to 5057.08 Mbps
Your PC/Workstation has a 121.0 KByte buffer which limits the throughput to 18.76 Mbps
The network based flow control limits the throughput to 18.98 Mbps

Client Data reports link is 'System Fault', Client Acks report link is 'System Fault'
Server Data reports link is 'System Fault', Server Acks report link is 'System Fault'

---

