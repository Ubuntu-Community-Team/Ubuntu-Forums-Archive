---
title: "Slight packet loss when using wireless network"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by SenH on 2008-02-28
I'm experiencing slight packet loss when using the wireless card. It's a bit annoying in an SSH session because the remote terminal will intermittently lock up for a few seconds.

I'm running Ubuntu 7.10 server on the latest Intel MacMini with the MadWifi drivers.
I'm only noticing a lot of PHY errors in athstats.

Ping remote terminal:
```
--- 10.0.1.5 ping statistics ---
570 packets transmitted, 547 received, 4% packet loss, time 569030ms
rtt min/avg/max/mdev = 0.716/1.756/247.609/11.342 ms

```

Ping gateway:
```
--- 10.0.1.1 ping statistics ---
554 packets transmitted, 526 received, 5% packet loss, time 553043ms
rtt min/avg/max/mdev = 0.641/0.788/13.917/0.901 ms

```

Version:
```
sen@kubrick:~$ uname -a
Linux kubrick 2.6.22-14-server #1 SMP Tue Feb 12 03:10:53 UTC 2008 x86_64 GNU/Linux

```

Netstat:
```
sen@kubrick:~$ netstat -s
Ip:
    6283 total packets received
    5 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    6278 incoming packets delivered
    5006 requests sent out
    7 dropped because of missing route
Icmp:
    1962 ICMP messages received
    45 input ICMP message failed.
    ICMP input histogram:
        echo requests: 251
        echo replies: 1666
    251 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        echo replies: 251
Tcp:
    0 active connections openings
    4 passive connection openings
    0 failed connection attempts
    0 connection resets received
    3 connections established
    3924 segments received
    3074 segments send out
    1 segments retransmited
    0 bad segments received.
    0 resets sent
Udp:
    16 packets received
    0 packets to unknown port received.
    0 packet receive errors
    16 packets sent
UdpLite:
TcpExt:
    6 packets rejects in established connections because of timestamp
    16 delayed acks sent
    Quick ack mode was activated 9 times
    8 packets directly queued to recvmsg prequeue.
    45 packet headers predicted
    58 acknowledgments not containing data received
    2925 predicted acknowledgments
    0 TCP data loss events
    1 other TCP timeouts
    9 DSACKs sent for old packets
IpExt:
    InBcastPkts: 421
    OutBcastPkts: 45

```

Athstats:
```
sen@kubrick:~$ athstats 
897 tx management frames
47 long on-chip tx retries
387 tx frames with no ack marked
8 tx frames with an alternate rate
3057 rx failed due to bad CRC
120984 PHY errors
    26268 OFDM timing
    94716 CCK timing
6460 periodic calibrations
rssi of last ack: 59
rssi of last rcv: 55
589 switched default/rx antenna
Antenna profile:
[1] tx     5533 rx    92341
[2] tx      132 rx     8370

```

Iwconfig:
```
sen@kubrick:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"xxxxxxxxxxx"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:93:EF:59:01   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-39 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

