---
title: "[SOLVED] Ping Rpeort Details"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Vishal Agarwal on 2008-10-26
> 10900 packets transmitted, 10580 received, +62 errors, 2% packet loss, time 26193600ms
rtt min/avg/max/mdev = 4.067/13.809/1834.822/38.994 ms


What are the meaning of:
1. rtt -> ?
2. min -> minimum
3. avg -> Agerage
4. max -> Maximum
5. mdev -> ?

What are the meaning of these first and last information in ping report. 

:confused:

---

### Post by caljohnsmith on 2008-10-26
Here's the breakdown:
[LIST]
[*]RTT = Round-trip time, or the time it takes from when you send the IP packet to when you receive a response.
[*]MIN = Of all the packets that you sent, whichever packet had the smallest RTT will be the MIN value
[*]MAX = Of all the packets that you sent, whichever packet had the largest RTT will be the MAX value
[*]AVG = average RTT of all the packets that you sent
[*]MDEV = the standard deviation of RTT for all the packets that you sent
[/LIST]

---

### Post by Vishal Agarwal on 2008-10-27
Thanks caljonsmith ! Thanks a lot.

---

