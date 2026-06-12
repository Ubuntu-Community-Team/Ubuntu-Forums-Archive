---
title: "Ping Problem"
date: 2017-07-22
forum: Networking &amp; Wireless
---

### Post by bizhat on 2017-07-22
I have 2 computers on LAN (WIFI). My computer IP is 192.168.1.2, other PC ip is 192.168.1.4, both are running Ubuntu 16.04 (updated to latest)

When i ping from 192.168.1.2 to 192.168.1.4 i get very high ping time=540 ms

When i login to other PC using SSH, then ping back, i get normal ping of time=3.07 ms

```

boby@hon-pc-01:~/Downloads$ ifconfig | grep "192.168.1."
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
boby@hon-pc-01:~/Downloads$ ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_seq=4 ttl=64 time=540 ms
64 bytes from 192.168.1.4: icmp_seq=5 ttl=64 time=406 ms
64 bytes from 192.168.1.4: icmp_seq=6 ttl=64 time=394 ms
64 bytes from 192.168.1.4: icmp_seq=7 ttl=64 time=417 ms
^C
--- 192.168.1.4 ping statistics ---
8 packets transmitted, 4 received, 50% packet loss, time 7023ms
rtt min/avg/max/mdev = 394.106/439.646/540.031/58.558 ms
boby@hon-pc-01:~/Downloads$ ssh root@192.168.1.4
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-83-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.

Last login: Sat Jul 22 10:26:55 2017 from 192.168.1.2
root@pc4:~# ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=3.07 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=2.39 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=6.91 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=2.23 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=2.81 ms
^C
--- 192.168.1.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 2.233/3.486/6.912/1.738 ms
root@pc4:~#

```

Any idea why this happens ?

---

### Post by TheFu on 2017-07-22
Local wifi interference?
Incorrect routing?
Incorrect gateway setting?
Conflicting DNS?

The **route** command output from both systems would be helpful.

---

### Post by bizhat on 2017-07-23
> **TheFu said:**
> Local wifi interference?

My place don't have any other wifi, so interference from other wifi. 

```

boby@hon-pc-01:~$ sudo iwlist wlxe8de270b3955 scan
wlxe8de270b3955  Scan completed :
          Cell 01 - Address: 60:E3:27:65:CF:AC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"HON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024c4d9b062
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0009484F53544F4E4E4554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050300080000
                    IE: Unknown: 2D1AFE1817FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F1600000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD800050F204104A0001101044000102103B0001031047001022087803ADF2BD11347BDF155D29E6D71021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180203040C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

boby@hon-pc-01:~$ 

```

Even if its wifi interference, won't it affect ping both ways ? The problem is only ping in one direction.

> **TheFu said:**
> Incorrect routing?

On PC 192.168.1.2

```

boby@hon-pc-01:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlxe8de270b3955
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 virbr0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxe8de270b3955
192.168.8.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s26f7u4
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
boby@hon-pc-01:~$ 

```

On PC 192.168.1.4

```

root@pc4:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1
root@pc4:~# 

```


Ping to gateway (192.168.1.1) from 192.168.1.4

```

root@pc4:~# ping -c  3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.18 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.43 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.68 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.436/1.767/2.186/0.316 ms
root@pc4:~# 

```

Ping to gateway (192.168.1.1) from 192.168.1.2

```

boby@hon-pc-01:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.01 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.79 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.91 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.795/1.907/2.015/0.103 ms
boby@hon-pc-01:~$

```

> **TheFu said:**
> Incorrect gateway setting?

I am not sure, from the route, it look like both PC use 192.168.1.1 as gateway.

> **TheFu said:**
> Conflicting DNS?

Since we use IP address to ping, DNS even relevant ?

---

