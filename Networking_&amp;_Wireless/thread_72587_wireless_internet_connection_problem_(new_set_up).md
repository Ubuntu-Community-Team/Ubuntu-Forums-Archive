---
title: "wireless internet connection problem (new set up)"
date: 2005-10-06
forum: Networking &amp; Wireless
---

### Post by imad_b on 2005-10-06
Hi,
I'm new to Ubuntu, (and Linux).
Got the 5.04 version of a magazine disc.

I have 2 hard drives, one running XP.
I created the ISO, and installed Ubuntu with no problems on my second HD.
Grub picks up at the beginning with no problems.

With XP, I can browse the internet no problems.
When I log into Ubuntu, when I try to browse it says "page can't be found".

I can ping my router ok (192.168.1.1)
But I can't log into my router.

Any ideas on what could be stopping me from browsing or logging into my router?
Any help appreciated.

I'm using a Netcom 5580W wireless router.

---

### Post by mlomker on 2005-10-07
What do you mean when you say that you can't log into your router?  You type the IP address into Firefox to get to a web interface on the router or something else?  Can you reach an address by number?

Try:
```

ping 209.98.65.80
ping www.mpr.org

```

You should get responses from the first one and the IP address and responses from the second.

```

root@mlomkernote:/ # ping 209.98.65.80
PING 209.98.65.80 (209.98.65.80) 56(84) bytes of data.
64 bytes from 209.98.65.80: icmp_seq=1 ttl=112 time=51.1 ms
64 bytes from 209.98.65.80: icmp_seq=2 ttl=112 time=44.5 ms
64 bytes from 209.98.65.80: icmp_seq=3 ttl=112 time=43.8 ms

--- 209.98.65.80 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 43.840/46.525/51.193/3.313 ms
root@mlomkernote:/ # ping www.mpr.org
PING www.mpr.org (209.98.65.80) 56(84) bytes of data.
64 bytes from 209.98.65.80: icmp_seq=1 ttl=112 time=54.0 ms
64 bytes from 209.98.65.80: icmp_seq=2 ttl=112 time=45.1 ms
64 bytes from 209.98.65.80: icmp_seq=3 ttl=112 time=46.3 ms

--- www.mpr.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 5621ms
rtt min/avg/max/mdev = 45.182/48.518/54.065/3.949 ms

```

---

### Post by imad_b on 2005-10-07
Thanks, got version 5.10, and installed it.
It now connects to the internet.
It also now showed the wireless connection profile, which it didn't do previously.

---

