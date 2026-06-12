---
title: "jumbo frames broken in update"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by clarknova on 2016-06-15
Ubuntu 16.04 LTS
Linux chunk 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

I have been dual-booting this laptop with Windows 7 Pro x64. In Ubuntu the mtu was set (through the GUI) to 4074. In Windows it is set to 4088. Jumbo frames are enabled in the switch and the mtu of the router interface is set to 4074. This has worked great for several weeks, but I noticed yesterday that in Ubuntu many web pages do not load completely, except after several reloads, or in some cases not at all. This is true also of my router's web UI, suggesting that the problem exists within my local network, between the laptop, wiring, switch and router.

I switched the mtu back to 1500 and this solved the problem. I switched back to 4074 and the problem immediately returned. I do not see the problem in Windows with the mtu left at 4088.

In Ubuntu, with the mtu set to 4074, I can do an mtu check by pinging the router thus:

```
$ ping -Mdo -s4046 -c3 10.130.8.254
PING 10.130.8.254 (10.130.8.254) 4046(4074) bytes of data.
4054 bytes from 10.130.8.254: icmp_seq=1 ttl=64 time=0.783 ms
4054 bytes from 10.130.8.254: icmp_seq=2 ttl=64 time=0.524 ms
4054 bytes from 10.130.8.254: icmp_seq=3 ttl=64 time=0.680 ms

--- 10.130.8.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.524/0.662/0.783/0.108 ms
```

This always succeeds, as if the mtu is fine. And yet, reducing the mtu in Ubuntu fixes the issue.

As I mentioned, I noticed this problem yesterday, but it is possible it has been going on for a week or more, as I haven't been in the office much this past week, and I did notice some page loading issues last week that I didn't have time to look into.

Can anybody recommend some further troubleshooting steps? Is anyone aware of any issues with recent updates that could be causing this?

---

