---
title: "Who produces this traffic and how to monitor it?"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by SebRok on 2008-03-27
I run ubnutu 7.10 on an Amilo notebook.
Everything works fine, but even when i don use any programs (no pidgin, no skype, no opera, no evolution) every minute or so there is a tremendous burst of etwork traffic, downstreamrates of 700 kbps for around 5 seconds.

what is this? who knows a tool to monitor applications'traffic usage??

thx in advance

---

### Post by Ryan450 on 2008-03-27
wow now that is an interesting one. 

I suppose you could run a packet sniffer on your ethernet device to capture and examine these packets. Although if your not too technically inclined the results may be a bit confusing. 

Etheral has always been a great tool for me to help identify such problems, specifically pay attention to the destination ports on the captured packets in the IP protocol, you can look them up on google to see what applications/services run them.

---

### Post by tgalati4 on 2008-03-27
>sudo apt-get install etherape

---

