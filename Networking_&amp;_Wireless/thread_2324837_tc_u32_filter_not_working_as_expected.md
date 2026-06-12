---
title: "tc u32 filter not working as expected"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by GEFORCEXTREME on 2016-05-16
Hi, I am trying to do bandwidth shaping on a topology consisting of a Ubuntu Server 14.04.04 LTS (A) acting as a WiFi AP, and two laptops B and C connecting to the network.
The following is the code I used on the AP (A).

```

tc qdisc add dev wlan0 root handle 1: htb default 12

tc class add dev wlan0 parent 1: classid 1:1 htb rate 10mbit
    
tc class add dev wlan0 parent 1:1 classid 1:10 htb rate 10mbit
tc class add dev wlan0 parent 1:1 classid 1:11 htb rate 5mbit
tc class add dev wlan0 parent 1:1 classid 1:12 htb rate 2mbit

tc filter add dev wlan0 protocol ip parent 1:0 prio 1 u32 match ip src 192.168.10.0/24 match ip dst 192.168.10.0/24 flowid 1:11
        
tc qdisc add dev wlan0 parent 1:10 sfq perturb 10
tc qdisc add dev wlan0 parent 1:11 sfq perturb 10
tc qdisc add dev wlan0 parent 1:12 sfq perturb 10

```

I want to limit internal network traffic on network 192.168.10.0/24. To test, I ran iperf on B as the server, and on C as the client. I found that iperf traffic goes to the default class, which is class 1:12. However, there is still some traffic going to class 1:11 when I do "tc -s qdisc ls dev wlan0", although it is not what I want to achieve.

What am I doing wrong?

---

### Post by GEFORCEXTREME on 2016-05-17
Update:

Ok, so I experimented with the u32 filter a bit and found that the following code only works for Internet traffic. 

```

tc filter add dev wlan0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.10.0/24 flowid 1:11

```

More specifically, I used speedtest.net to test the download speed and it is correctly filtered and throttled. However, internal network traffic which should have destination 192.168.10.XXX is not filtered by the filter and directed to the correct class.

---

