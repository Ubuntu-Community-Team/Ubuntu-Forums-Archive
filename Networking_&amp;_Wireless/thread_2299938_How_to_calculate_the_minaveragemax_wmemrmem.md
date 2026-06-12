---
title: "How to calculate the min/average/max wmem/rmem?"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by nick97 on 2015-10-22
hi to all
I am trying to calculate the average rmem /wmem and max rmem/wmem.
So with the information below 


1


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500


root@lenovo-Ideapad-Z570:/home/lenovo# ping -c5 google.com
PING google.com (74.125.133.101) 56(84) bytes of data.
64 bytes from wo-in-f101.1e100.net (74.125.133.101): icmp_seq=1 ttl=44 time=63.9 ms
64 bytes from wo-in-f101.1e100.net (74.125.133.101): icmp_seq=2 ttl=44 time=111 ms
64 bytes from wo-in-f101.1e100.net (74.125.133.101): icmp_seq=3 ttl=44 time=66.3 ms
64 bytes from wo-in-f101.1e100.net (74.125.133.101): icmp_seq=4 ttl=44 time=77.5 ms
64 bytes from wo-in-f101.1e100.net (74.125.133.101): icmp_seq=5 ttl=44 time=65.9 ms


--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 63.936/77.107/111.740/17.958 ms


and 2


net.ipv4.tcp_rmem = 10240       87380   12582912
net.ipv4.tcp_wmem = 10240       87380   12582912
net.ipv4.udp_mem = 138129       184174  276258




with the help of the function:


BDP = max bandwidth of your internet connection (Bytes/second) * RTT (seconds)


i can calculate the average value for my internet cpnnection of 12MBps


But how can i calculate the maximum?

---

