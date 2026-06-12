---
title: "Megavideo website doesn't load AT ALL..."
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Slickshoes023 on 2010-08-17
I am using ubuntu 10.04.. my problem is that all website work perfectly fine, except for megavideo.. i noticed how when i click links to watch a megavideo, it just continues to load... it doesn't say time expired or site not available.. i checked on the "it's just you" website to see if megavideo is running, and it says its up and running...

I also ping [www.megavideo.com](www.megavideo.com)

it showed 
PING [www.megavideo.com](www.megavideo.com) (174.140.154.24) 56(84) bytes of data.
and continues to blink...

then i Ping 174.140.154.24
it did nothing, continued to blink like it was loading...

someone help please!!! i use megavideo frequently, and now its useless...
please be elaborate, cuz im in a "Absolute Beginner Talk" Thread.
Thnx - Shawn

---

### Post by KIAaze on 2010-08-19
Do sites like youtube work for you?
Did you install flash?: [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Megavideo works without any problems (except streaming slowly) for me.
I just have to click on the play button twice (opens an ad on the first click).

Note: I use the noscript add-on. Some scripts might prevent you from using megavideo correctly...

P.S.: This is what a working ping should look like:
```
[^_^][2][me@laptop][~]$  ping www.megavideo.com
PING www.megavideo.com (174.140.154.22) 56(84) bytes of data.

64 bytes from 174.140.154.22: icmp_seq=1 ttl=56 time=153 ms
64 bytes from 174.140.154.22: icmp_seq=2 ttl=56 time=235 ms
64 bytes from 174.140.154.22: icmp_seq=3 ttl=56 time=154 ms
64 bytes from 174.140.154.22: icmp_seq=4 ttl=56 time=157 ms
64 bytes from 174.140.154.22: icmp_seq=5 ttl=56 time=156 ms
^C64 bytes from 174.140.154.22: icmp_seq=6 ttl=56 time=194 ms

--- www.megavideo.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 26151ms
rtt min/avg/max/mdev = 153.764/175.263/235.541/30.474 ms
[^_^][3][me@laptop][~]$  ping 174.140.154.22
PING 174.140.154.22 (174.140.154.22) 56(84) bytes of data.
64 bytes from 174.140.154.22: icmp_seq=1 ttl=56 time=156 ms
64 bytes from 174.140.154.22: icmp_seq=2 ttl=56 time=153 ms
64 bytes from 174.140.154.22: icmp_seq=3 ttl=56 time=153 ms
64 bytes from 174.140.154.22: icmp_seq=4 ttl=56 time=153 ms
^C
--- 174.140.154.22 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 153.076/154.399/156.626/1.362 ms
[^_^][4][me@laptop][~]$  ping 174.140.154.24
PING 174.140.154.24 (174.140.154.24) 56(84) bytes of data.
64 bytes from 174.140.154.24: icmp_seq=1 ttl=56 time=322 ms
64 bytes from 174.140.154.24: icmp_seq=3 ttl=56 time=356 ms
64 bytes from 174.140.154.24: icmp_seq=4 ttl=56 time=152 ms
^C
--- 174.140.154.24 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3007ms
rtt min/avg/max/mdev = 152.715/277.329/356.497/89.185 ms
```

If this is not your case, you have a network problem (or megavideo is filtered out by your ISP?).

---

### Post by Slickshoes023 on 2010-09-03
yah i really think they did filter it out? so how can i unfilter it without them doing anything.. im in india, and its the worst ****in ISP ever dude. **** my ISP... they do that ****.. i dont care if i have to go through extreme measures to get my megavideo back, what do i do?

---

