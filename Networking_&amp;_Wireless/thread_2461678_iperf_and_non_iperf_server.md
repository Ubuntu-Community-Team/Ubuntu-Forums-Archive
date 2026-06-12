---
title: "iperf and non iperf server"
date: 2021-05-05
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2021-05-05
Ubuntu 18:04 LTS

Folks,

Main machine is an Ubuntu laptop but I have 4 RaspberryPi devices on my network

Been experimenting with a few iperf V2 options and sent the following command to a Pi

```
iperf -c 10.19.44.12 -p 80 -t 30 -i 5
------------------------------------------------------------
Client connecting to 10.19.44.12, TCP port 80
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 10.19.44.114 port 47606 connected with 10.19.44.12 port 80
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec  26.1 MBytes  43.8 Mbits/sec
[  3]  5.0-10.0 sec  23.4 MBytes  39.2 Mbits/sec
[  3] 10.0-15.0 sec  24.0 MBytes  40.3 Mbits/sec
[  3] 15.0-20.0 sec  25.0 MBytes  41.9 Mbits/sec
[  3] 20.0-25.0 sec  26.5 MBytes  44.5 Mbits/sec
[  3] 25.0-30.0 sec  24.8 MBytes  41.5 Mbits/sec
[  3]  0.0-30.0 sec   150 MBytes  41.8 Mbits/sec


```

Got the expected result but seems I had stopped the server running on the target device, I do however, have apache server running on that Pi.

Decided to try on some other servers, mixed results.

Device running TVHeadend on port 9981 gave list similar to above (Different MBPS).

Router gave one reading then said broken pipe.

Can iperf be usefully used with servers other than a corresponding iperf server?

Geoff

---

