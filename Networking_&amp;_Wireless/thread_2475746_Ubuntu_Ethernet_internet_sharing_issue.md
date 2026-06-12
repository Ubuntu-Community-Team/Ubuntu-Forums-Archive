---
title: "Ubuntu Ethernet internet sharing issue"
date: 2022-06-07
forum: Networking &amp; Wireless
---

### Post by zerosynergy on 2022-06-07
Attempting to share my Ubuntu systems internet with another pc over Ethernet. My Ubuntu system gets its internet from another Ethernet adapter and I want to use its secondary adapter to share internet with another computer. Now I’ve watched a few videos and it just basically says to create a Ethernet connection and under ipv4 chose method: share to other computers this creates a IP address of 10.42.0.1 on ubuntu for the adapter to my windows pc I’m share to however my windows pc only ever gives me a 169. ip instead and I’ve attempted to create a static ip of 10.42.0.1 or 10.42.0.2 but windows won’t give me internet. 

Any suggestions? Am I doing this right or do I need some kind of bridging?

Edit: Gave up my windows pc is being a pain, tried bridging using netplan and even tried nmtui but no luck took another approach and used link aggregation from my router to the server lose a bit of speed doing that but less of a headache.

---

