---
title: "No path to us.archive.ubuntu.com"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by MikeBenza on 2007-02-18
My machine can't find a path to us.archive.ubuntu.com:
```

mike@ubuntu:/etc/resolvconf/run$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (195.248.90.35) 56(84) bytes of data.
From byrd.canonical.com (91.189.88.11) icmp_seq=2 Destination Host Unreachable
From byrd.canonical.com (91.189.88.11) icmp_seq=3 Destination Host Unreachable
From byrd.canonical.com (91.189.88.11) icmp_seq=4 Destination Host Unreachable
From byrd.canonical.com (91.189.88.11) icmp_seq=7 Destination Host Unreachable
From byrd.canonical.com (91.189.88.11) icmp_seq=8 Destination Host Unreachable

--- us.archive.ubuntu.com ping statistics ---
9 packets transmitted, 0 received, +5 errors, 100% packet loss, time 8018ms
, pipe 3

```When I try to update in aptitude, the specific problem is no path to host.  Another problem with the machine is that resolv.conf gets hosed every few days (I've just removed all write permissions on it...lets see if that helps), but right now it's set up correctly and can resolve other names:

```

PING [www.ubuntu.com]("http://www.ubuntu.com") (82.211.81.166) 56(84) bytes of data.
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=1 ttl=48 time=83.0 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=2 ttl=48 time=89.1 ms

```

For now, I've switched to ca.archive.ubuntu.org, but I can probably get better speeds out of us.  Any advice?

- Mike

---

