---
title: "ping command not working"
date: 2017-03-21
forum: Networking &amp; Wireless
---

### Post by John_Patrick_Mason on 2017-03-21
I tried disabling Gufw, but I still can't get it to work.

Here's what I tried to do:
```

ping google.com
PING google.com (172.217.10.142) 56(84) bytes of data.
^C
--- google.com ping statistics ---
58 packets transmitted, 0 received, 100% packet loss, time 58358ms

```

---

### Post by vasa1 on 2017-03-21
Post ```
sudo ufw status verbose
```

---

### Post by John_Patrick_Mason on 2017-03-21
Well, I just disabled the firewall again, so:

```
Status: inactive
```

If I don't disable the firewall I get:

```
Status: active
Logging: on (low)
Default: reject (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

Either way, ping doesn't work. Maybe disabling the firewall and restarting a couple of times would work?

---

### Post by Doug S on 2017-03-22
Is there a router between your computer and the internet? Often, by default, they do not allow ping.
Use tcpdump (or wireshark, if you prefer) to observe what is going on at the packet level. Example:

one terminal:```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]ping google.com[/COLOR]
PING google.com (172.217.3.174) 56(84) bytes of data.
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=1 ttl=57 time=32.8 ms
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=2 ttl=57 time=32.8 ms
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=3 ttl=57 time=32.2 ms
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=4 ttl=57 time=31.8 ms
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=5 ttl=57 time=31.8 ms
64 bytes from sea15s11-in-f174.1e100.net (172.217.3.174): icmp_seq=6 ttl=57 time=32.1 ms
^C
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 31.884/32.305/32.864/0.410 ms

```another terminal:```
doug@s15:~/c$ [COLOR="#FF0000"]sudo tcpdump -tttt -n -i enp3s0 icmp[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on enp3s0, link-type EN10MB (Ethernet), capture size 262144 bytes
2017-03-22 14:26:54.401827 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 1, length 64
2017-03-22 14:26:54.434679 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 1, length 64
2017-03-22 14:26:55.403225 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 2, length 64
2017-03-22 14:26:55.436005 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 2, length 64
2017-03-22 14:26:56.405091 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 3, length 64
2017-03-22 14:26:56.437338 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 3, length 64
2017-03-22 14:26:57.406501 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 4, length 64
2017-03-22 14:26:57.438361 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 4, length 64
2017-03-22 14:26:58.407525 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 5, length 64
2017-03-22 14:26:58.439385 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 5, length 64
2017-03-22 14:26:59.408565 IP 192.168.111.112 > 172.217.3.174: ICMP echo request, id 8610, seq 6, length 64
2017-03-22 14:26:59.440666 IP 172.217.3.174 > 192.168.111.112: ICMP echo reply, id 8610, seq 6, length 64
```

---

### Post by John_Patrick_Mason on 2017-03-22
I just figured it out. It was my router. I had to lower its security settings to get it to work. Thanks anyway.

---

