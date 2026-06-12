---
title: "QCA6174 performance degrades after a while [ubuntu 20.04]"
date: 2021-12-22
forum: Networking &amp; Wireless
---

### Post by ugtar on 2021-12-22
Hello, I'm trying to debug an issue I'm experiencing with performance
degredation on my wifi adapter. After some time (I haven't been able to
pinpoint anything specific), my wifi speed drops and latency starts spiking
like crazy.

Here is what it looks like currently:
```
# ugtar@scrappy3: ~
&#62560; speed-test 

       Ping   84 ms
   Download   16 Mbps
     Upload   7.9 Mbps
```

I can ping the wireless AP I'm currently connected to:
```
# ugtar@scrappy3: ~
&#62560; ping -c 30 192.168.0.185
PING 192.168.0.185 (192.168.0.185) 56(84) bytes of data.
64 bytes from 192.168.0.185: icmp_seq=1 ttl=64 time=119 ms
64 bytes from 192.168.0.185: icmp_seq=2 ttl=64 time=143 ms
64 bytes from 192.168.0.185: icmp_seq=3 ttl=64 time=2.08 ms
64 bytes from 192.168.0.185: icmp_seq=4 ttl=64 time=2.81 ms
64 bytes from 192.168.0.185: icmp_seq=5 ttl=64 time=28.3 ms
64 bytes from 192.168.0.185: icmp_seq=6 ttl=64 time=2.04 ms
64 bytes from 192.168.0.185: icmp_seq=7 ttl=64 time=2.66 ms
64 bytes from 192.168.0.185: icmp_seq=8 ttl=64 time=72.9 ms
64 bytes from 192.168.0.185: icmp_seq=9 ttl=64 time=97.1 ms
64 bytes from 192.168.0.185: icmp_seq=10 ttl=64 time=137 ms
64 bytes from 192.168.0.185: icmp_seq=11 ttl=64 time=3.23 ms
64 bytes from 192.168.0.185: icmp_seq=12 ttl=64 time=2.08 ms
64 bytes from 192.168.0.185: icmp_seq=13 ttl=64 time=14.3 ms
64 bytes from 192.168.0.185: icmp_seq=14 ttl=64 time=1.79 ms
64 bytes from 192.168.0.185: icmp_seq=15 ttl=64 time=124 ms
64 bytes from 192.168.0.185: icmp_seq=16 ttl=64 time=149 ms
64 bytes from 192.168.0.185: icmp_seq=17 ttl=64 time=2.03 ms
64 bytes from 192.168.0.185: icmp_seq=18 ttl=64 time=1.80 ms
64 bytes from 192.168.0.185: icmp_seq=19 ttl=64 time=33.1 ms
64 bytes from 192.168.0.185: icmp_seq=20 ttl=64 time=1.89 ms
64 bytes from 192.168.0.185: icmp_seq=21 ttl=64 time=4.25 ms
64 bytes from 192.168.0.185: icmp_seq=22 ttl=64 time=3.27 ms
64 bytes from 192.168.0.185: icmp_seq=23 ttl=64 time=107 ms
64 bytes from 192.168.0.185: icmp_seq=24 ttl=64 time=131 ms
64 bytes from 192.168.0.185: icmp_seq=25 ttl=64 time=1.82 ms
64 bytes from 192.168.0.185: icmp_seq=26 ttl=64 time=3.15 ms
64 bytes from 192.168.0.185: icmp_seq=27 ttl=64 time=16.0 ms
64 bytes from 192.168.0.185: icmp_seq=28 ttl=64 time=2.72 ms
64 bytes from 192.168.0.185: icmp_seq=29 ttl=64 time=3.21 ms
64 bytes from 192.168.0.185: icmp_seq=30 ttl=64 time=2.03 ms

--- 192.168.0.185 ping statistics ---
30 packets transmitted, 30 received, 0% packet loss, time 29038ms
rtt min/avg/max/mdev = 1.789/40.488/148.638/54.035 ms
```


By contrast, an old macbook I have sitting right next to this one looks like
this (connected to the same AP):
```
# ugtar@Old-MacBook-Pro-5 : ~
$ speedtest
Retrieving speedtest.net configuration...
Testing from Spectrum (REMOVED IP)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by i3D.net (Newark, NJ) [20.97 km]: 23.502 ms
Testing download speed................................................................................
Download: 192.97 Mbit/s
Testing upload speed......................................................................................................
Upload: 11.83 Mbit/s


# ugtar@Old-MacBook-Pro-5 : ~
$ ping -c 30 192.168.0.185
PING 192.168.0.185 (192.168.0.185): 56 data bytes
64 bytes from 192.168.0.185: icmp_seq=0 ttl=64 time=3.252 ms
64 bytes from 192.168.0.185: icmp_seq=1 ttl=64 time=3.404 ms
64 bytes from 192.168.0.185: icmp_seq=2 ttl=64 time=3.519 ms
64 bytes from 192.168.0.185: icmp_seq=3 ttl=64 time=3.451 ms
64 bytes from 192.168.0.185: icmp_seq=4 ttl=64 time=3.499 ms
64 bytes from 192.168.0.185: icmp_seq=5 ttl=64 time=3.533 ms
64 bytes from 192.168.0.185: icmp_seq=6 ttl=64 time=3.437 ms
64 bytes from 192.168.0.185: icmp_seq=7 ttl=64 time=3.317 ms
64 bytes from 192.168.0.185: icmp_seq=8 ttl=64 time=3.464 ms
64 bytes from 192.168.0.185: icmp_seq=9 ttl=64 time=3.631 ms
64 bytes from 192.168.0.185: icmp_seq=10 ttl=64 time=3.350 ms
64 bytes from 192.168.0.185: icmp_seq=11 ttl=64 time=3.393 ms
64 bytes from 192.168.0.185: icmp_seq=12 ttl=64 time=4.300 ms
64 bytes from 192.168.0.185: icmp_seq=13 ttl=64 time=3.670 ms
64 bytes from 192.168.0.185: icmp_seq=14 ttl=64 time=3.494 ms
64 bytes from 192.168.0.185: icmp_seq=15 ttl=64 time=3.506 ms
64 bytes from 192.168.0.185: icmp_seq=16 ttl=64 time=0.690 ms
64 bytes from 192.168.0.185: icmp_seq=17 ttl=64 time=1.181 ms
64 bytes from 192.168.0.185: icmp_seq=18 ttl=64 time=3.490 ms
64 bytes from 192.168.0.185: icmp_seq=19 ttl=64 time=3.479 ms
64 bytes from 192.168.0.185: icmp_seq=20 ttl=64 time=3.509 ms
64 bytes from 192.168.0.185: icmp_seq=21 ttl=64 time=3.540 ms
64 bytes from 192.168.0.185: icmp_seq=22 ttl=64 time=3.546 ms
64 bytes from 192.168.0.185: icmp_seq=23 ttl=64 time=3.434 ms
64 bytes from 192.168.0.185: icmp_seq=24 ttl=64 time=3.461 ms
64 bytes from 192.168.0.185: icmp_seq=25 ttl=64 time=3.473 ms
64 bytes from 192.168.0.185: icmp_seq=26 ttl=64 time=3.403 ms
64 bytes from 192.168.0.185: icmp_seq=27 ttl=64 time=3.507 ms
64 bytes from 192.168.0.185: icmp_seq=28 ttl=64 time=3.536 ms
64 bytes from 192.168.0.185: icmp_seq=29 ttl=64 time=3.514 ms

--- 192.168.0.185 ping statistics ---
30 packets transmitted, 30 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.690/3.333/4.300/0.666 ms
```


After rebooting my laptop, things go back to normal for a while. Logging out,
disconnecting and reconnecting to my AP, or bringing the wireless interface up
and down doesn't seem to help, only a reboot.

After rebooting it looks like this:
```
# ugtar@scrappy3: ~
&#62560; speed-test 

       Ping   47 ms
   Download   153 Mbps
     Upload   12 Mbps

# ugtar@scrappy3: ~
&#62560; ping -c 30 192.168.0.185
PING 192.168.0.185 (192.168.0.185) 56(84) bytes of data.
64 bytes from 192.168.0.185: icmp_seq=1 ttl=64 time=5.96 ms
64 bytes from 192.168.0.185: icmp_seq=2 ttl=64 time=1.97 ms
64 bytes from 192.168.0.185: icmp_seq=3 ttl=64 time=3.59 ms
64 bytes from 192.168.0.185: icmp_seq=4 ttl=64 time=28.7 ms
64 bytes from 192.168.0.185: icmp_seq=5 ttl=64 time=1.92 ms
64 bytes from 192.168.0.185: icmp_seq=6 ttl=64 time=2.14 ms
64 bytes from 192.168.0.185: icmp_seq=7 ttl=64 time=2.00 ms
64 bytes from 192.168.0.185: icmp_seq=8 ttl=64 time=2.00 ms
64 bytes from 192.168.0.185: icmp_seq=9 ttl=64 time=2.01 ms
64 bytes from 192.168.0.185: icmp_seq=10 ttl=64 time=2.01 ms
64 bytes from 192.168.0.185: icmp_seq=11 ttl=64 time=5.51 ms
64 bytes from 192.168.0.185: icmp_seq=12 ttl=64 time=2.41 ms
64 bytes from 192.168.0.185: icmp_seq=13 ttl=64 time=3.33 ms
64 bytes from 192.168.0.185: icmp_seq=14 ttl=64 time=2.07 ms
64 bytes from 192.168.0.185: icmp_seq=15 ttl=64 time=3.23 ms
64 bytes from 192.168.0.185: icmp_seq=16 ttl=64 time=2.09 ms
64 bytes from 192.168.0.185: icmp_seq=17 ttl=64 time=3.42 ms
64 bytes from 192.168.0.185: icmp_seq=18 ttl=64 time=3.61 ms
64 bytes from 192.168.0.185: icmp_seq=19 ttl=64 time=3.43 ms
64 bytes from 192.168.0.185: icmp_seq=20 ttl=64 time=3.23 ms
64 bytes from 192.168.0.185: icmp_seq=21 ttl=64 time=2.03 ms
64 bytes from 192.168.0.185: icmp_seq=22 ttl=64 time=1.90 ms
64 bytes from 192.168.0.185: icmp_seq=23 ttl=64 time=1.86 ms
64 bytes from 192.168.0.185: icmp_seq=24 ttl=64 time=3.42 ms
64 bytes from 192.168.0.185: icmp_seq=25 ttl=64 time=1.97 ms
64 bytes from 192.168.0.185: icmp_seq=26 ttl=64 time=3.55 ms
64 bytes from 192.168.0.185: icmp_seq=27 ttl=64 time=3.62 ms
64 bytes from 192.168.0.185: icmp_seq=28 ttl=64 time=3.91 ms
64 bytes from 192.168.0.185: icmp_seq=29 ttl=64 time=2.10 ms
64 bytes from 192.168.0.185: icmp_seq=30 ttl=64 time=3.37 ms

--- 192.168.0.185 ping statistics ---
30 packets transmitted, 30 received, 0% packet loss, time 29049ms
rtt min/avg/max/mdev = 1.862/3.745/28.727/4.752 ms
```


I have tried installing multiple different firmware versions with no apparent
difference, and also running different kernel versions. I haven't seen anything
suspicious in syslog or dmesg, but maybe I just don't know what to look for.

I've attached the output of the wireless-info script.

TIA,
Ugtar

---

### Post by praseodym on 2021-12-23
Obviously a roaming issue with 4 APs named "foobar". Use the correct APs MAC address and add it into the network manager profile under "BSSID"

---

### Post by ugtar on 2021-12-26
I did already consider that. There are 4 APs named foobar because I have two unifi APs on the network with both 2.4ghz and 5ghz networks, but this laptop (the one with the performance issue) is using a fixed bssid (in network manager settings). I've been using a fixed bssid for a while already to prevent the laptop from roaming.

---

### Post by ugtar on 2022-01-05
hey, sorry if you're getting double-pinged but i don't know if you saw my reply. short answer is, it's not a roaming issue, the connection has been using a set MAC address for the BSSID. I'm wondering if you have any other suggestions for where I could look to debug this?

---

