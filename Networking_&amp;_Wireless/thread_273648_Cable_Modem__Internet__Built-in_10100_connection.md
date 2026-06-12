---
title: "Cable Modem / Internet / Built-in 10/100 connection"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by zpro on 2006-10-08
There is something serious wrong with Edgy networking connection, via ethernet (built-in) ( could be driver related) that is effecting downloading, within a short time, the connection STOPs ( can't even ping out ) have to reboot the machine, then all is well... have included some stat's for a Network Guru, to figure this one out. ( or maybe) edgy is still very buggy. 

just would like to surf, with out rebooting every 30 mins or so.  Please note: did not have this problem with Dapper 6.0.6.1 at all.

Thanks -:confused: :-k 

PS:
when using ifconfig ( compare to window ipconfig) in windows, 
we could release and renew, how does one do this in Linux ???
----

rick@KB32bit:~$ ifconfig
eth0 * * *Link encap:Ethernet *HWaddr 00:03:25:28:93:B3
* * * * * inet addr:24.92.160.221 *Bcast:255.255.255.255 *Mask:255.255.248.0
* * * * * UP BROADCAST RUNNING MULTICAST *MTU:576 *Metric:1
* * * * * RX packets:21605 errors:0 dropped:0 overruns:0 frame:3
* * * * * TX packets:12296 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:1000
* * * * * RX bytes:8014066 (7.6 MiB) *TX bytes:952583 (930.2 KiB)
* * * * * Interrupt:50

lo * * * *Link encap:Local Loopback
* * * * * inet addr:127.0.0.1 *Mask:255.0.0.0
* * * * * inet6 addr: ::1/128 Scope:Host
* * * * * UP LOOPBACK RUNNING *MTU:16436 *Metric:1
* * * * * RX packets:0 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:0
* * * * * RX bytes:0 (0.0 b) *TX bytes:0 (0.0 b)

netstat -i
Iface * MTU Met * RX-OK RX-ERR RX-DRP RX-OVR * *TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0 * *576 0 * * 22082 * * *0 * * *0 * * *0 * *12296 * * *0 * * *0 * * *0 
BMRU
lo * *16436 0 * * * * 0 * * *0 * * *0 * * *0 * * * *0 * * *0 * * *0 * * *0 LRU

netstat -s
rick@KB32bit:~$ netstat -s
Ip:
* * 12836 total packets received
* * 2 with invalid addresses
* * 0 forwarded
* * 0 incoming packets discarded
* * 12834 incoming packets delivered
* * 12316 requests sent out
Icmp:
* * 0 ICMP messages received
* * 0 input ICMP message failed.
* * ICMP input histogram:
* * 5 ICMP messages sent
* * 0 ICMP messages failed
* * ICMP output histogram:
* * * * destination unreachable: 5
Tcp:
* * 13 active connections openings
* * 0 passive connection openings
* * 0 failed connection attempts
* * 0 connection resets received
* * 0 connections established
* * 12750 segments received
* * 12259 segments send out
* * 8 segments retransmited
* * 11 bad segments received.
* * 4 resets sent
Udp:
* * 106 packets received
* * 5 packets to unknown port received.
* * 0 packet receive errors
* * 52 packets sent
TcpExt:
* * 6 TCP sockets finished time wait in fast timer
* * 25 delayed acks sent
* * Quick ack mode was activated 2 times
* * 5602 packet headers predicted
* * 26 acknowledgments not containing data received
* * 218 predicted acknowledgments
* * 0 TCP data loss events
* * 1 other TCP timeouts
* * 2 DSACKs sent for old packets
* * 1 connections aborted due to timeout

---

### Post by zpro on 2006-10-08
please... this is a network issue.. anyone
:???:

---

### Post by mips on 2006-10-09
And should really be in the edgy forum seeing it is beta.

---

### Post by zpro on 2006-10-09
Well, there no edgy forum that I can see,
show me the link... nothing on the main page.
:rolleyes:

---

### Post by mips on 2006-10-09
[http://www.ubuntuforums.org/forumdisplay.php?f=177](http://www.ubuntuforums.org/forumdisplay.php?f=177)   :rolleyes:

---

