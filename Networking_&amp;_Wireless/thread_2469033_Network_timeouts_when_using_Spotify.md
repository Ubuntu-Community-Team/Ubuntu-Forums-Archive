---
title: "Network timeouts when using Spotify"
date: 2021-11-17
forum: Networking &amp; Wireless
---

### Post by the-markus on 2021-11-17
I'm using Kubuntu 21.04 and always get network timeouts when opening or using Spotify.

Example:

```

PING 10.0.0.200 (10.0.0.200) 56(84) bytes of data.
64 bytes from 10.0.0.200: icmp_seq=1 ttl=64 time=2.79 ms
64 bytes from 10.0.0.200: icmp_seq=2 ttl=64 time=2.00 ms
64 bytes from 10.0.0.200: icmp_seq=3 ttl=64 time=1.33 ms
no answer yet for icmp_seq=4
no answer yet for icmp_seq=5
no answer yet for icmp_seq=6
64 bytes from 10.0.0.200: icmp_seq=7 ttl=64 time=1.53 ms
64 bytes from 10.0.0.200: icmp_seq=8 ttl=64 time=1.47 ms
^C
--- 10.0.0.200 ping statistics ---
8 packets transmitted, 5 received, 37.5% packet loss, time 7058ms
rtt min/avg/max/mdev = 1.332/1.822/2.785/0.530 ms

```

So far I have only had this issue with Spotify and only when I'm connected to my wifi repeater.

I have contacted the support of my repeater manufacturer (they said they can't see an issue with my repeater or router), tried using an ubuntu live usb (still the same issue) and installing a different version of Spotify (snap and Spotify repo, still no luck).

When I'm running tcpdump it is like frozen as soon as the timeouts happen and I can't even ctrl-c to exit.

I don't know how to deal with this problem further because there aren't any errors in syslog or dmesg.

Thanks for any help.

---

### Post by slickymaster on 2021-11-18
Thread moved to **Networking & Wireless** for a better fit

---

