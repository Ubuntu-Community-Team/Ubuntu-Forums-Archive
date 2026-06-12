---
title: "Samba with 10Gbe (SSD to SSD) Upload 350, download 80!"
date: 2018-03-31
forum: Networking &amp; Wireless
---

### Post by egandt on 2018-03-31
Samba with 10Gbe (SSD to SSD) Upload 350, download 80!
Samba is trying to kill me.  I upgraded to 10Gbe Intell x550-T2 cards with a Netgear 16Port 10Bge switch.
Setup was smooth, since then it has been nothing but painful.

Currently I can get Samba shares to write Windows->Linux at about 350MB a second (which is still slow as each drive can do 500+), I've confirmed that Samba is using version 3.1.1 (so it supports multiple streams), yet Linux->Windows speeds max out around 80MB (that is worse that I got with a 1Gbe connection (about 92 on Avg.)
I'm simply at a lost to explain why one way is 350 and the other is 80, I've tested using iperf and I get 1.1Gib cleanly through the NIC's so that is not the limitation.

I've tried Network tuning on Linux and Windows without any measurable change other than enabling Jumbo frames (which boosted download from 200 to 350MB).

Also something I've noticed if Linux is rebooted then the Samba shares from Window never reconnect until I restart Windows, they simply act as if the server is not responding, but if I restart Window (poof everything works again).

I'd like more than 350MB, but I can live with that if I can get bi-directional which is not happening.

OS and software versions:
Windows 10 1709 (March Update)
Ubuntu 16.04LTS, Samba: 4.3.11-Ubuntu
Connection protocol is  3.1.1 checking from Windows.

Any suggestions?
EIC

---

### Post by egandt on 2018-04-01
I was able to improve sending to about 150 by setting the transmit buffered to 16384 on Windows however even so it is less than half the read speed.

I've played with Linux network settings as well, for 10Gbe:
# Maximum receive socket buffer size
net.core.rmem_max = 134217728
# Maximum send socket buffer size
net.core.wmem_max = 134217728
# increase Linux autotuning TCP buffer limit to 64MB
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864
# Maximum number of packets queued on the input side
net.core.netdev_max_backlog = 300000
# Auto tuning
net.ipv4.tcp_moderate_rcvbuf =1
# Don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
# The Hamilton TCP (HighSpeed-TCP) algorithm is a packet loss based congestion control and is more aggressive pushing up to max bandwidth (total BDP) and favors hosts with lower TTL / VARTTL.
net.ipv4.tcp_congestion_control=htcp
# If you are using jumbo frames set this to avoid MTU black holes.
net.ipv4.tcp_mtu_probing = 1
# recommended for CentOS7/Debian8 hosts
net.core.default_qdisc = fq

With little change, not sure if they are worth it even.


Did a quick test with NFS should should be as good or better, but from Windows it is peaks at 75 and runs closer to 40MB/s.
ERIC

---

