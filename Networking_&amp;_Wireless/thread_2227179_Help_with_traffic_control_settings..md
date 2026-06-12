---
title: "Help with traffic control settings."
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by Faizan_Agha on 2014-05-31
URGENT: I would really appreciate the help on that:


E.g. To introduce 35ms delay with 1024/1024 (down/up) Kbps rate I use:


sudo wondershaper wlan0 1024 1024

sudo tc qdisc add dev wlan0 root netem delay 35ms 


and get the error:
RTNETLINK answers: File exists



Can somebody please help on that? I have been struggling a lot on this one!

Thx
Faizan

---

### Post by coffeecat on 2014-05-31
Moved to own thread, and given suitable title.

---

### Post by Faizan_Agha on 2014-06-01
Log after a successful attempt on ubuntu 13.1:

faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc mq 0: root 
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 root handle 1: htb default 12
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc htb 1: root refcnt 5 r2q 10 default 12 direct_packets_stat 0
faizan@faizan-Q470C-500P4C:~$ sudo tc class add dev wlan0 parent 1:1 classid 1:12 htb rate 20kbps ceil 20kbps
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc htb 1: root refcnt 5 r2q 10 default 12 direct_packets_stat 33
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0^C
faizan@faizan-Q470C-500P4C:~$ ping -s 192.168.1.1
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
faizan@faizan-Q470C-500P4C:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.553 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.514 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.535 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.546 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=0.568 ms


--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.514/0.543/0.568/0.023 ms
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 parent 1:12 netem delay 1000ms
[sudo] password for faizan: 
faizan@faizan-Q470C-500P4C:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1000 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=1000 ms
^C
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2001ms
rtt min/avg/max/mdev = 1000.536/1000.546/1000.557/1.000 ms
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 root netem delay 100ms^C
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 root netem delay 100ms
RTNETLINK answers: File exists
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 parent 1:12 netem delay 100ms
RTNETLINK answers: File exists
faizan@faizan-Q470C-500P4C:~$ ping -c 192.168.1.1
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
faizan@faizan-Q470C-500P4C:~$ ping -c 192.168.1.1
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
faizan@faizan-Q470C-500P4C:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1000 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=1000 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=1000 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3001ms
rtt min/avg/max/mdev = 1000.502/1000.528/1000.569/0.817 ms
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 handle ffff: ingress
faizan@faizan-Q470C-500P4C:~$ tc filter add dev $DEV parent ffff: protocol ip prio 50 u32 match ip src \
>    0.0.0.0/0 police rate ${DOWNLINK}kbit burst 10k drop flowid :1
Unknown filter "ffff:", hence option "protocol" is unparsable
faizan@faizan-Q470C-500P4C:~$ tc filter add dev wlan0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 4096kbit burst 10k drop flowid :1
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
faizan@faizan-Q470C-500P4C:~$ sudo tc filter add dev wlan0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 4096kbit burst 10k drop flowid :1
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc htb 1: root refcnt 5 r2q 10 default 12 direct_packets_stat 33
qdisc netem 8013: parent 1:12 limit 1000 delay 1.0s
qdisc ingress ffff: parent ffff:fff1 ---------------- 
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc del dev wlan0
RTNETLINK answers: No such file or directory
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc add dev wlan0 parent 1:12 netem delay 100ms^Cfaizan@faizan-Q470C-500P4C:~$ sudo tc qdisc del dev wlan0 parent 1:12
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc htb 1: root refcnt 5 r2q 10 default 12 direct_packets_stat 33
qdisc ingress ffff: parent ffff:fff1 ---------------- 
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc del dev wlan0 root
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0
qdisc mq 0: root 
qdisc ingress ffff: parent ffff:fff1 ---------------- 
faizan@faizan-Q470C-500P4C:~$ sudo tc qdisc show dev wlan0

---

