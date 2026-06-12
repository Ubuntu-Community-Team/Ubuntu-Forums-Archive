---
title: "Packet loss after installing python-wicd update"
date: 2014-10-23
forum: Networking &amp; Wireless
---

### Post by steveparbkk on 2014-10-23
Since the installation of:-

python-wicd (1.7.2.4-4.1ubuntu1,automatic);
wicd-gtk (1.7.2.4-4.1unbuntu1); and,
wicd-daemon (1.7.2.4-4.1ubuntu1,automatic)

I have been experiencing packet loss on my wired NIC.  Fortunately my wireless NIC appears to be working just fine.  At first I thought it was a hardware failure (until I realized that the problem occurred immediately after the new wicd installation - and I realized what wicd is).

Here's the output from ping:

```

steven@steven-Veriton-X480G:~$ ping 192.168.100.1 -c100
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.

--- 192.168.100.1 ping statistics ---
100 packets transmitted, 0 received, 100% packet loss, time 99791ms

```

and

```

steven@steven-Veriton-X480G:~$ ping 127.0.0.1 -c100
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.032 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=11 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=12 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=13 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=14 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=15 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=16 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=17 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=18 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=19 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_seq=20 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=21 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=22 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=23 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=24 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=25 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=26 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=27 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=28 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=29 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=30 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=31 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=32 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=33 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=34 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=35 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=36 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=37 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=38 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=39 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=40 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=41 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=42 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=43 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=44 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=45 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=46 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=47 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=48 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=49 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=50 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=51 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=52 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=53 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=54 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=55 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=56 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=57 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=58 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=59 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=60 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=61 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=62 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=63 ttl=64 time=0.083 ms
64 bytes from 127.0.0.1: icmp_seq=64 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=65 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_seq=66 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=67 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=68 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=69 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=70 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=71 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=72 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=73 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=74 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=75 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=76 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=77 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=78 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=79 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=80 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=81 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=82 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=83 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=84 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=85 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=86 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=87 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=88 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=89 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=90 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_seq=91 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=92 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=93 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=94 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=95 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=96 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=97 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=98 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=99 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=100 ttl=64 time=0.042 ms

--- 127.0.0.1 ping statistics ---
100 packets transmitted, 100 received, 0% packet loss, time 98997ms
rtt min/avg/max/mdev = 0.022/0.038/0.083/0.006 ms

```

Actually, total packet loss is unusual.  It is usually just intermittent.

See:

```

steven@steven-Veriton-X480G:~$ ping 192.168.100.1 -c100
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.
64 bytes from 192.168.100.1: icmp_seq=9 ttl=64 time=70.8 ms
64 bytes from 192.168.100.1: icmp_seq=10 ttl=64 time=8.03 ms
64 bytes from 192.168.100.1: icmp_seq=11 ttl=64 time=17.9 ms
64 bytes from 192.168.100.1: icmp_seq=12 ttl=64 time=8.22 ms
64 bytes from 192.168.100.1: icmp_seq=13 ttl=64 time=3.64 ms
64 bytes from 192.168.100.1: icmp_seq=14 ttl=64 time=16.4 ms
64 bytes from 192.168.100.1: icmp_seq=15 ttl=64 time=26.5 ms
64 bytes from 192.168.100.1: icmp_seq=16 ttl=64 time=3.38 ms
64 bytes from 192.168.100.1: icmp_seq=17 ttl=64 time=3.53 ms
64 bytes from 192.168.100.1: icmp_seq=18 ttl=64 time=3.49 ms
64 bytes from 192.168.100.1: icmp_seq=19 ttl=64 time=12.8 ms
64 bytes from 192.168.100.1: icmp_seq=20 ttl=64 time=20.8 ms
64 bytes from 192.168.100.1: icmp_seq=21 ttl=64 time=30.0 ms
64 bytes from 192.168.100.1: icmp_seq=22 ttl=64 time=20.9 ms
64 bytes from 192.168.100.1: icmp_seq=23 ttl=64 time=8.11 ms
64 bytes from 192.168.100.1: icmp_seq=24 ttl=64 time=29.8 ms
64 bytes from 192.168.100.1: icmp_seq=25 ttl=64 time=8.41 ms
64 bytes from 192.168.100.1: icmp_seq=26 ttl=64 time=26.5 ms
64 bytes from 192.168.100.1: icmp_seq=27 ttl=64 time=7.58 ms
64 bytes from 192.168.100.1: icmp_seq=28 ttl=64 time=6.93 ms
64 bytes from 192.168.100.1: icmp_seq=29 ttl=64 time=37.1 ms
64 bytes from 192.168.100.1: icmp_seq=30 ttl=64 time=23.8 ms
64 bytes from 192.168.100.1: icmp_seq=31 ttl=64 time=3.52 ms
64 bytes from 192.168.100.1: icmp_seq=32 ttl=64 time=3.58 ms
64 bytes from 192.168.100.1: icmp_seq=33 ttl=64 time=21.2 ms
64 bytes from 192.168.100.1: icmp_seq=34 ttl=64 time=21.2 ms
64 bytes from 192.168.100.1: icmp_seq=35 ttl=64 time=21.1 ms
64 bytes from 192.168.100.1: icmp_seq=36 ttl=64 time=21.3 ms
64 bytes from 192.168.100.1: icmp_seq=37 ttl=64 time=19.9 ms
64 bytes from 192.168.100.1: icmp_seq=38 ttl=64 time=3.97 ms
64 bytes from 192.168.100.1: icmp_seq=39 ttl=64 time=8.38 ms
64 bytes from 192.168.100.1: icmp_seq=40 ttl=64 time=8.41 ms
64 bytes from 192.168.100.1: icmp_seq=41 ttl=64 time=8.24 ms
64 bytes from 192.168.100.1: icmp_seq=42 ttl=64 time=17.4 ms
64 bytes from 192.168.100.1: icmp_seq=43 ttl=64 time=4.64 ms
64 bytes from 192.168.100.1: icmp_seq=44 ttl=64 time=14.9 ms
64 bytes from 192.168.100.1: icmp_seq=45 ttl=64 time=14.3 ms
64 bytes from 192.168.100.1: icmp_seq=46 ttl=64 time=3.63 ms
64 bytes from 192.168.100.1: icmp_seq=47 ttl=64 time=3.63 ms
64 bytes from 192.168.100.1: icmp_seq=48 ttl=64 time=8.12 ms
64 bytes from 192.168.100.1: icmp_seq=98 ttl=64 time=3.27 ms
64 bytes from 192.168.100.1: icmp_seq=99 ttl=64 time=10.3 ms
64 bytes from 192.168.100.1: icmp_seq=100 ttl=64 time=32.0 ms

--- 192.168.100.1 ping statistics ---
100 packets transmitted, 43 received, 57% packet loss, time 99512ms
rtt min/avg/max/mdev = 3.271/15.093/70.853/12.660 ms

```

I'm not sure what else might be helpful.  Here's ifconfig in case that is useful.

```

eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94  
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1134331 (1.1 MB)  TX bytes:792627 (792.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1899554 (1.8 MB)  TX bytes:1899554 (1.8 MB)

wlan0     Link encap:Ethernet  HWaddr c4:a8:1d:03:66:f2  
          inet addr:192.168.100.3  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::c6a8:1dff:fe03:66f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:266596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:157911312 (157.9 MB)  TX bytes:53443118 (53.4 MB)

```

And here's the same trace over the wlan0

```

steven@steven-Veriton-X480G:~$ ping 192.168.100.1 -c100
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.
64 bytes from 192.168.100.1: icmp_seq=1 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=2 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=3 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=4 ttl=64 time=9.29 ms
64 bytes from 192.168.100.1: icmp_seq=5 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=6 ttl=64 time=1.40 ms
64 bytes from 192.168.100.1: icmp_seq=7 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=8 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=9 ttl=64 time=2.03 ms
64 bytes from 192.168.100.1: icmp_seq=10 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=11 ttl=64 time=1.30 ms
64 bytes from 192.168.100.1: icmp_seq=12 ttl=64 time=1.30 ms
64 bytes from 192.168.100.1: icmp_seq=13 ttl=64 time=9.81 ms
64 bytes from 192.168.100.1: icmp_seq=14 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=15 ttl=64 time=1.30 ms
64 bytes from 192.168.100.1: icmp_seq=16 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=17 ttl=64 time=1.75 ms
64 bytes from 192.168.100.1: icmp_seq=18 ttl=64 time=1.29 ms
64 bytes from 192.168.100.1: icmp_seq=19 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=20 ttl=64 time=6.40 ms
64 bytes from 192.168.100.1: icmp_seq=22 ttl=64 time=4.55 ms
64 bytes from 192.168.100.1: icmp_seq=23 ttl=64 time=2.23 ms
64 bytes from 192.168.100.1: icmp_seq=24 ttl=64 time=1.88 ms
64 bytes from 192.168.100.1: icmp_seq=25 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=26 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=27 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=28 ttl=64 time=1.44 ms
64 bytes from 192.168.100.1: icmp_seq=29 ttl=64 time=2.12 ms
64 bytes from 192.168.100.1: icmp_seq=30 ttl=64 time=1.38 ms
64 bytes from 192.168.100.1: icmp_seq=31 ttl=64 time=5.54 ms
64 bytes from 192.168.100.1: icmp_seq=32 ttl=64 time=3.60 ms
64 bytes from 192.168.100.1: icmp_seq=33 ttl=64 time=8.83 ms
64 bytes from 192.168.100.1: icmp_seq=35 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=36 ttl=64 time=1.37 ms
64 bytes from 192.168.100.1: icmp_seq=38 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=39 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=40 ttl=64 time=2.02 ms
64 bytes from 192.168.100.1: icmp_seq=41 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=42 ttl=64 time=1.38 ms
64 bytes from 192.168.100.1: icmp_seq=43 ttl=64 time=1.41 ms
64 bytes from 192.168.100.1: icmp_seq=44 ttl=64 time=2.61 ms
64 bytes from 192.168.100.1: icmp_seq=45 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=46 ttl=64 time=1.37 ms
64 bytes from 192.168.100.1: icmp_seq=47 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=48 ttl=64 time=1.45 ms
64 bytes from 192.168.100.1: icmp_seq=49 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=50 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=51 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=52 ttl=64 time=1.31 ms
64 bytes from 192.168.100.1: icmp_seq=53 ttl=64 time=1.58 ms
64 bytes from 192.168.100.1: icmp_seq=54 ttl=64 time=11.8 ms
64 bytes from 192.168.100.1: icmp_seq=55 ttl=64 time=2.02 ms
64 bytes from 192.168.100.1: icmp_seq=56 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=57 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=58 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=59 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=60 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=61 ttl=64 time=1.83 ms
64 bytes from 192.168.100.1: icmp_seq=62 ttl=64 time=1.29 ms
64 bytes from 192.168.100.1: icmp_seq=63 ttl=64 time=7.89 ms
64 bytes from 192.168.100.1: icmp_seq=64 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=65 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=66 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=67 ttl=64 time=1.35 ms
64 bytes from 192.168.100.1: icmp_seq=68 ttl=64 time=1.51 ms
64 bytes from 192.168.100.1: icmp_seq=69 ttl=64 time=1.73 ms
64 bytes from 192.168.100.1: icmp_seq=70 ttl=64 time=1.65 ms
64 bytes from 192.168.100.1: icmp_seq=71 ttl=64 time=4.69 ms
64 bytes from 192.168.100.1: icmp_seq=72 ttl=64 time=7.91 ms
64 bytes from 192.168.100.1: icmp_seq=73 ttl=64 time=1.49 ms
64 bytes from 192.168.100.1: icmp_seq=74 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=75 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=76 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=77 ttl=64 time=1.36 ms
64 bytes from 192.168.100.1: icmp_seq=78 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=79 ttl=64 time=1.52 ms
64 bytes from 192.168.100.1: icmp_seq=80 ttl=64 time=1.30 ms
64 bytes from 192.168.100.1: icmp_seq=81 ttl=64 time=5.95 ms
64 bytes from 192.168.100.1: icmp_seq=82 ttl=64 time=1.48 ms
64 bytes from 192.168.100.1: icmp_seq=83 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=84 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=85 ttl=64 time=1.49 ms
64 bytes from 192.168.100.1: icmp_seq=86 ttl=64 time=1.32 ms
64 bytes from 192.168.100.1: icmp_seq=87 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=88 ttl=64 time=2.04 ms
64 bytes from 192.168.100.1: icmp_seq=89 ttl=64 time=1.68 ms
64 bytes from 192.168.100.1: icmp_seq=90 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=91 ttl=64 time=1.33 ms
64 bytes from 192.168.100.1: icmp_seq=92 ttl=64 time=1.30 ms
64 bytes from 192.168.100.1: icmp_seq=93 ttl=64 time=1.37 ms
64 bytes from 192.168.100.1: icmp_seq=94 ttl=64 time=1.61 ms
64 bytes from 192.168.100.1: icmp_seq=95 ttl=64 time=1.37 ms
64 bytes from 192.168.100.1: icmp_seq=96 ttl=64 time=1.34 ms
64 bytes from 192.168.100.1: icmp_seq=97 ttl=64 time=1.50 ms
64 bytes from 192.168.100.1: icmp_seq=98 ttl=64 time=5.16 ms
64 bytes from 192.168.100.1: icmp_seq=99 ttl=64 time=10.7 ms
64 bytes from 192.168.100.1: icmp_seq=100 ttl=64 time=1.33 ms

--- 192.168.100.1 ping statistics ---
100 packets transmitted, 97 received, 3% packet loss, time 99133ms
rtt min/avg/max/mdev = 1.295/2.304/11.842/2.267 ms

```

I should perhaps add that I will be travelling for about two week (leaving in about 18 hours) and so I will be away from this box until I return.

Annoyingly, after imagining that the problem was hardware related I bought an Intel NIC which conflicted with the on-board graphic card, as otherwise I might not have realized that wicd is the network manager.  Once I saw that the problems tarted immediately after installing the new version of wicd, I realised that it almost certainly isn't a hardware issue.  

Thanks for any insights.

---

