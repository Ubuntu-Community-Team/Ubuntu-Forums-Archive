---
title: "PulseAudio multicast stream disrupts internet connection"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by justarrow on 2008-06-14
It seems like my router just looses its ability to access internet as soon as I stream audio over my wireless network using PulseAudio 0.9.10 (hardy amd64). The problem has got me completely baffled, since I still can reach local addresses and the router itself. Any attempts to access outside addresses just times out and pinging gives "unknown host"-messages. The obvious conclusion (but not necessarily the problem) is that the host lookup is somehow disrupted by the multicast stream - stopping the stream and everything works flawlessly. I have a D-Link DIR-655 router and use WPA2 encryption.

Thanks in advance for any theories and suggestions!

---

