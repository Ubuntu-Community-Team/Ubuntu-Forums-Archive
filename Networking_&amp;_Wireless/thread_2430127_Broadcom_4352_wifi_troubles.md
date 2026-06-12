---
title: "Broadcom 4352 wifi troubles?"
date: 2019-10-28
forum: Networking &amp; Wireless
---

### Post by eezacque on 2019-10-28
I have used wifi problem-free for years, but since a few weeks my network seems to have come to a grinding halt, with ping times as high as several 10s of seconds. Another computer on the same network works like a charm, so I can safely rule out problems with internet provider, modem or wifi. All I can see is that the package loss in communicating with my cable modem runs as high as 10%.

Another symptom that puzzles me is that 'nmcli d wifi' yields a list of all wifi networks in the neighbourhood, but after a while it lists only my own network. The complete list doesn't become available until I reset my wifi. 

I'm puzzled, and don't even know where to start. Does it look like my Broadcom 4352 is slowly passing out?

---

### Post by praseodym on 2019-10-28
Please run the wireless script from the sticky thread and show the outputs

---

### Post by eezacque on 2019-10-28
Got it sorted out. For reasons unknown to me, Ubuntu had switched to the 5GHz band, which doesn't work well here. Switching to 2.4GHz solved it for me.

---

