---
title: "slow internet, windows fine"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by DocForbin on 2008-01-29
For about a week I've been experiencing slow download rates, though oddly the upload is fine. It is typically 200-300 kbps down using a speed test from my ISP, and 400-500 up. Today a cable guy came out and ran some tests. With his windows laptop he consistently got 5-6 mbps, 20x what I get running 7.10. Here's what I've tried so far:

- made sure ipv6 was disabled
- manually entered the DNS servers for my ISP
- swapped network cables. I get the same problem wireless or wired

Any ideas?

---

### Post by DocForbin on 2008-01-29
Probably unrelated, but I noticed some ipv6 stuff in my hosts file.

adam@lucinda:~$ ip a | grep inet6
adam@lucinda:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 lucinda

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by DocForbin on 2008-01-29
I went ahead and tried commenting those lines in my hosts file, no luck.

---

### Post by bladesuk1 on 2008-01-31
i can connect to the internet via my wireless card just fine, and initially it runs at 3.5mbps.  however, after a short while, it drops down to around 1mpbs instead.

i've tried turning off everything that even remotely hints at ipv6, and i've also tried using my isp's dns servers instead of the connection automatically pointing at the router.

weirdly, if i disconnect from the network using network manager, and then connect to it again, the speed goes back up to around 3mbps, before dropping back down again a few minutes later.

i'm just going to try it with a wired connection to see if it does the same thing or not - i'll post in here and let you know.

b

---

### Post by bladesuk1 on 2008-01-31
i've tried with the wired connection, and it seems that the same thing is still happening.

it seems to me like it's some sort of issue with the network manager, or something it uses - feels like it's filling something up, and then reconnecting temporarily clears it out before it fills back up again.  very odd.

---

