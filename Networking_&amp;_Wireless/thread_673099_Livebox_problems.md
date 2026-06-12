---
title: "Livebox problems"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by regua on 2008-01-20
Hi.

I have a Livebox router, and a few computers at my home. The ones with Windows (XP) on them can connect to the Internet. I, on Ubuntu 7.10, cannot.

Today I got a new Livebox as the previous one stopped working properly, so I started configuring it. I entered the network's SSID, the WEP key, set IP to be automatically downloaded (DHCP), and... nothing.

When I ping the router (192.168.1.1), I get a strange message:
```
[~]$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.3.193 icmp_seq=1 Destination Host Unreachable
From 169.254.3.193 icmp_seq=2 Destination Host Unreachable
From 169.254.3.193 icmp_seq=3 Destination Host Unreachable
```
I was curious about the strange IP that Livebox assigned to me, so I set it manually in the connection settings (manually set IPs never work with Livebox, I just wanted to give it a try).
```
[~]$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.15 icmp_seq=2 Destination Host Unreachable
From 192.168.1.15 icmp_seq=3 Destination Host Unreachable
```
As you can see, it behaves the same.

Then, I tried pinging google.com.
```
[~]$ ping google.com
ping: unknown host google.com
```
After that, I pinged a random IP:
```
[~]$ ping 212.68.1.1
PING 212.68.1.1 (212.68.1.1) 56(84) bytes of data.
From 169.254.3.193 icmp_seq=1 Destination Host Unreachable
From 169.254.3.193 icmp_seq=2 Destination Host Unreachable
From 169.254.3.193 icmp_seq=3 Destination Host Unreachable
```

Why does the router behave like this? Why can't I connect to the Internet (and to the router)?
Is it the router's fault? If yes, why the Windows-based computers can connect properly?

Thanks.

---

