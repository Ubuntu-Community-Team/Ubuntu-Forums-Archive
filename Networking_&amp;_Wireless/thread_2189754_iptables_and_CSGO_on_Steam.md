---
title: "iptables and CSGO on Steam"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by brandon-bilbo on 2013-11-23
Hopefully some of you here are gamers and can feel my pain. 

I have a cable modem coming into my ubuntu server 12.04 with 2 NICs acting as a gateway/router for the rest of my home network. I can join casual games, browse community servers and join them, join a random deathmatch, all that jazz, basically everything the game has to offer. But when I do queue in competitive matchmaking it will not let me connect. I've tried forwarding the ports suggested on steam's website along with many other ports suggested by others with no success. Actually when I forward the ports suggested on steams site, it will not even let me connect to steam at all.. If I bypass my ubuntu server and connect strait to the modem, works fine. windows firewall is disabled. 

here are some logs from iptables while its trying to connect. 192.69.97.217 is the IP of the matchmaking server im failing to connect with.
```

Nov 23 18:25:31 provizon kernel: [  285.732015] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62829 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4427 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:25:31 provizon kernel: [  286.124102] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=51 TOS=0x00 PREC=0x00 TTL=127 ID=4436 PROTO=UDP SPT=27005 DPT=27038 LEN=31
Nov 23 18:25:31 provizon kernel: [  286.200256] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=92 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=27038 DPT=27005 LEN=72
Nov 23 18:25:31 provizon kernel: [  286.225776] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=1055 TOS=0x00 PREC=0x00 TTL=127 ID=4437 PROTO=UDP SPT=27005 DPT=27038 LEN=1035
Nov 23 18:25:37 provizon kernel: [  291.876083] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62830 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4429 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:25:37 provizon kernel: [  292.240423] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=51 TOS=0x00 PREC=0x00 TTL=127 ID=4438 PROTO=UDP SPT=27005 DPT=27038 LEN=31
Nov 23 18:25:37 provizon kernel: [  292.309826] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=92 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=27038 DPT=27005 LEN=72
Nov 23 18:25:37 provizon kernel: [  292.343062] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=1055 TOS=0x00 PREC=0x00 TTL=127 ID=4439 PROTO=UDP SPT=27005 DPT=27038 LEN=1035
Nov 23 18:25:43 provizon kernel: [  298.020354] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62831 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4431 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:25:43 provizon kernel: [  298.357598] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=51 TOS=0x00 PREC=0x00 TTL=127 ID=4440 PROTO=UDP SPT=27005 DPT=27038 LEN=31
Nov 23 18:25:44 provizon kernel: [  298.481284] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=92 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=27038 DPT=27005 LEN=72
Nov 23 18:25:44 provizon kernel: [  298.510261] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=1055 TOS=0x00 PREC=0x00 TTL=127 ID=4441 PROTO=UDP SPT=27005 DPT=27038 LEN=1035
Nov 23 18:25:49 provizon kernel: [  304.168090] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62832 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4433 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:25:50 provizon kernel: [  304.522828] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=51 TOS=0x00 PREC=0x00 TTL=127 ID=4442 PROTO=UDP SPT=27005 DPT=27038 LEN=31
Nov 23 18:25:50 provizon kernel: [  304.591250] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=92 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=27038 DPT=27005 LEN=72
Nov 23 18:25:50 provizon kernel: [  304.624497] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=1055 TOS=0x00 PREC=0x00 TTL=127 ID=4443 PROTO=UDP SPT=27005 DPT=27038 LEN=1035
Nov 23 18:25:55 provizon kernel: [  310.181052] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62833 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4435 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:25:56 provizon kernel: [  310.669294] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=51 TOS=0x00 PREC=0x00 TTL=127 ID=4444 PROTO=UDP SPT=27005 DPT=27038 LEN=31
Nov 23 18:25:56 provizon kernel: [  310.746951] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=92 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=27038 DPT=27005 LEN=72
Nov 23 18:25:56 provizon kernel: [  310.772086] BANDWIDTH_OUT:IN=LAN OUT=WAN MAC=00:1e:4f:fa:78:02:10:bf:48:87:16:98:08:00 SRC=192.168.0.40 DST=192.69.97.217 LEN=1055 TOS=0x00 PREC=0x00 TTL=127 ID=4445 PROTO=UDP SPT=27005 DPT=27038 LEN=1035
Nov 23 18:26:01 provizon kernel: [  316.323710] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62834 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4437 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:26:08 provizon kernel: [  322.467637] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62835 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4439 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:26:14 provizon kernel: [  328.612051] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62836 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4441 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:26:20 provizon kernel: [  334.756572] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62837 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4443 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
Nov 23 18:26:26 provizon kernel: [  340.899513] BANDWIDTH_IN:IN=WAN OUT=LAN MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=192.69.97.217 DST=192.168.0.40 LEN=576 TOS=0x00 PREC=0x20 TTL=52 ID=62838 PROTO=ICMP TYPE=11 CODE=1 [SRC=192.168.0.40 DST=192.69.97.217 LEN=572 TOS=0x00 PREC=0x00 TTL=116 ID=4445 MF PROTO=UDP SPT=27005 DPT=27038 LEN=1035 ]
provizon@provizon:~$ cat /var/log/bandwidth | grep -i -e 192.69.97.217 -e dropped
Nov 23 18:11:40 provizon kernel: [   19.428193] Dropped by firewall: IN= OUT=LAN SRC=192.168.0.3 DST=224.0.0.251 LEN=192 TOS=0x00 PREC=0x00 TTL=255 ID=10049 DF PROTO=UDP SPT=5353 DPT=5353 LEN=172
Nov 23 18:11:40 provizon kernel: [   19.463281] Dropped by firewall: IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29284 DF PROTO=TCP SPT=54280 DPT=631 WINDOW=32792 RES=0x00 SYN URGP=0
Nov 23 18:11:40 provizon kernel: [   19.463313] Dropped by firewall: IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=22523 DF PROTO=TCP SPT=631 DPT=54280 WINDOW=0 RES=0x00 ACK RST URGP=0
Nov 23 18:11:40 provizon kernel: [   19.472606] Dropped by firewall: IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=37128 DF PROTO=TCP SPT=48172 DPT=953 WINDOW=32792 RES=0x00 SYN URGP=0
Nov 23 18:11:40 provizon kernel: [   19.472636] Dropped by firewall: IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=22524 DF PROTO=TCP SPT=953 DPT=48172 WINDOW=0 RES=0x00 ACK RST URGP=0
Nov 23 18:11:42 provizon kernel: [   22.311779] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=96.40.196.250 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=115 ID=13357 PROTO=UDP SPT=63068 DPT=13201 LEN=60
Nov 23 18:11:42 provizon kernel: [   22.322893] Dropped by firewall: IN=WAN OUT= MAC= SRC=98.196.115.73 DST=224.0.0.251 LEN=293 TOS=0x00 PREC=0x00 TTL=255 ID=10048 DF PROTO=UDP SPT=5353 DPT=5353 LEN=273
Nov 23 18:11:42 provizon kernel: [   22.324124] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=76.185.180.81 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=116 ID=24994 PROTO=UDP SPT=55743 DPT=62219 LEN=60
Nov 23 18:11:43 provizon kernel: [   22.385448] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=216.58.17.53 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=115 ID=31596 PROTO=UDP SPT=49681 DPT=13201 LEN=60
Nov 23 18:11:43 provizon kernel: [   22.393252] Dropped by firewall: IN=WAN OUT= MAC= SRC=98.196.115.73 DST=224.0.0.251 LEN=192 TOS=0x00 PREC=0x00 TTL=255 ID=10049 DF PROTO=UDP SPT=5353 DPT=5353 LEN=172
Nov 23 18:11:44 provizon kernel: [   23.430009] Dropped by firewall: IN= OUT=WAN SRC=98.196.115.73 DST=69.171.239.12 LEN=79 TOS=0x00 PREC=0x00 TTL=64 ID=55072 PROTO=UDP SPT=62127 DPT=53 LEN=59
Nov 23 18:11:46 provizon kernel: [   26.340169] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=216.58.17.53 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=115 ID=32372 PROTO=UDP SPT=49681 DPT=13201 LEN=60
Nov 23 18:11:48 provizon kernel: [   27.440972] Dropped by firewall: IN= OUT=WAN SRC=98.196.115.73 DST=83.109.254.106 LEN=108 TOS=0x00 PREC=0xC0 TTL=64 ID=28543 PROTO=ICMP TYPE=3 CODE=3 [SRC=83.109.254.106 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=106 ID=26288 PROTO=UDP SPT=63664 DPT=13201 LEN=60 ]
Nov 23 18:11:51 provizon kernel: [   30.438435] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=109.189.141.22 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=105 ID=1584 PROTO=UDP SPT=52720 DPT=13201 LEN=60
Nov 23 18:11:52 provizon kernel: [   31.464867] Dropped by firewall: IN= OUT=WAN SRC=98.196.115.73 DST=94.245.121.251 LEN=112 TOS=0x00 PREC=0xC0 TTL=64 ID=30917 PROTO=ICMP TYPE=3 CODE=3 [SRC=94.245.121.251 DST=98.196.115.73 LEN=84 TOS=0x00 PREC=0x20 TTL=48 ID=19219 PROTO=UDP SPT=3544 DPT=62219 LEN=64 ]
Nov 23 18:11:55 provizon kernel: [   34.571702] Dropped by firewall: IN=WAN OUT= MAC=10:fe:ed:03:99:73:00:13:7f:31:c0:98:08:00 SRC=188.4.131.126 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=115 ID=29575 PROTO=UDP SPT=64472 DPT=13201 LEN=60
Nov 23 18:11:56 provizon kernel: [   35.440047] Dropped by firewall: IN= OUT=WAN SRC=98.196.115.73 DST=70.64.73.196 LEN=108 TOS=0x00 PREC=0xC0 TTL=64 ID=11691 PROTO=ICMP TYPE=3 CODE=3 [SRC=70.64.73.196 DST=98.196.115.73 LEN=80 TOS=0x00 PREC=0x20 TTL=116 ID=29344 PROTO=UDP SPT=57448 DPT=13201 LEN=60 ]

```

---

### Post by Doug S on 2013-11-24
For others reading this thread, the OP's iptables rule set is on [another thread]("http://ubuntuforums.org/showthread.php?t=2189640").

Certainly, ICMP type 11 (Time Exceeded) code 1 (Fragment Reassembly Time Exceeded) is a strange one. It is not clear to me what is wrong. I would be tempted to capture packets using tcpdump or wireshark to help investigate further.

For your iptables rules set, I would suggest: add an unconditional lo interface destination ACCEPT to the OUTPUT chain; Only use any given log prefix once, as it makes it more difficult to correlate the log entry back to the rule set when the same prefix is re-used; specify WAN source in your port forwarding PREROUTING rules.

---

### Post by brandon-bilbo on 2013-11-24
This issue is now my top priority, but testing is limited since I have to take a ban everytime.. sigh. Will have a chance to try again tomorrow evening. 

Here are my current iptable rules. 

sudo iptables -v -x -n -L
```

Chain INPUT (policy DROP 22081 packets, 1494878 bytes)
    pkts      bytes       target     prot opt    in     out     source               destination
    3835   837517       ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
     237    16066        ACCEPT     all  --    lo      *       0.0.0.0/0            0.0.0.0/0
 2540484 2485237070 ACCEPT     all  --   LAN    *       0.0.0.0/0            0.0.0.0/0
   30568  6403263      ACCEPT     all  --   WAN    *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       3      128           ACCEPT     tcp --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
   11116  4070377      ACCEPT     udp --  WAN    *       73.0.0.0/8           0.0.0.0/0            udp spts:67:68 dpts:67:68
    1383   112691       LOG          udp --  WAN    *       0.0.0.0/0            0.0.0.0/0            udp  spts:1:30000 dpts:1:30000 limit: avg 15/sec burst 5 LOG flags 0 level 7 prefix "DROPPED_IN:"
     626    33248        LOG          tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp spts:1:30000 dpts:1:30000 limit: avg 15/sec burst 5 LOG flags 0 level 7 prefix "DROPPED_IN:"


Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
 7818564 1787102027 ACCEPT     all  --  LAN    WAN     0.0.0.0/0            0.0.0.0/0
 7810694 9556566382 ACCEPT     all  --  WAN    LAN     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp          dpt:8000
    2449   150454 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp         dpt:56666
   13607  1716878 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp        dpt:56666
       0        0 LOG        all  --  WAN    *       0.0.0.0/0            0.0.0.0/0            lim     it: avg 60/sec burst 5 LOG flags 0 level 7 prefix "DROPPED_IN (forwarded):"


Chain OUTPUT (policy ACCEPT 1737199 packets, 9458810432 bytes)
    pkts      bytes target     prot opt in     out     source               destination

```

sudo iptables -t nat -v -x -n -L
```

Chain PREROUTING (policy ACCEPT 83365 packets, 6470825 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:192.168.0.30:8000
    2462   151150 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666 to:192.168.0.30:56666
   12893  1626482 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666 to:192.168.0.30:56666


Chain INPUT (policy ACCEPT 2477 packets, 289748 bytes)
    pkts      bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 7396 packets, 548299 bytes)
    pkts      bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 15428 packets, 1787192 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   66548  5253012 MASQUERADE  all  --  *      WAN     0.0.0.0/0            0.0.0.0/0

```

Any and all suggestions are helpful as this is my first experience with iptables. I tried to get the formatting to look decent with the iptables for your viewing but it looks like it didnt do much help.

---

### Post by Doug S on 2013-11-25
> **brandon-bilbo said:**
> This issue is now my top priority, but testing is limited since I have to take a ban everytime.. sigh.What does "take a ban" mean?

for this:```
Chain PREROUTING (policy ACCEPT 83365 packets, 6470825 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:192.168.0.30:8000
    2462   151150 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666 to:192.168.0.30:56666
   12893  1626482 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666 to:192.168.0.30:56666
```I still suggest this:```
Chain PREROUTING (policy ACCEPT 83365 packets, 6470825 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DNAT       tcp  --  [COLOR=#ff0000]WAN[/COLOR]      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:192.168.0.30:8000
    2462   151150 DNAT       tcp  --  [COLOR=#ff0000]WAN[/COLOR]      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666 to:192.168.0.30:56666
   12893  1626482 DNAT       udp  --  [COLOR=#ff0000]WAN[/COLOR]      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666 to:192.168.0.30:56666
```For example, here is my one port forward:```
Chain PREROUTING (policy ACCEPT 570207 packets, 49138643 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       6      288 DNAT       tcp  --  [COLOR=#ff0000]eth1[/COLOR]   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8083 to:192.168.111.112:80
```There may still be other iptables issues, I might look again later, or someone else might comment.

I would still suggest to use a packet sniffer to acquire your attempts with 192.69.97.217. In one terminal:```
sudo tcpdump -n -tttt -i WAN host 192.69.97.217
```in another terminal:```
sudo tcpdump -n -tttt -i LAN host 192.69.97.217
```Where you replace WAN and LAN with your actual interface names. You might also want to redirect the output to files, if there is a lot.
Or, if you don't mind the stuff intermixed, just do this:```
sudo tcpdump -n -tttt [COLOR=#ff0000]-i any[/COLOR] host 192.69.97.217
```Myself, I prefer it separated by interface, but if all your NAT is working properly, intermixed might be clearer in this case.

---

### Post by brandon-bilbo on 2013-11-26
"take a ban" means that when I dont connect to the matchmade game after a couple of minutes they ban me from queuing in competitive for a period of time. its a bitch.

Doug, I would like to extend mass amounts of gratitude to you. Thanks to you, I have resolved this issue. Using tcpdump I saw this crap being put out  

 ICMP ip reassembly time exceeded, length 556

quick google search shows that its my MTU setting on the WAN adapter. it was low like 400 or 500 range. Set it to 1500 and hell yes! back to pwning nubs!!! you are freakin awesome my man.

This also solved my other problem on a different thread limiting my upload speed. Double thumbs up bro! I'd buy you several drinks if I could.

---

