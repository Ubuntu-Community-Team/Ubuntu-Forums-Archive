---
title: "Streaming using Multiple Network Interface Card Problem"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by shuaibe on 2007-07-03
Hello,

I have a RTSP streaming setup, in which Iam using Feisty Fawn as OS on both the server and client machine. Iam using Apple's DSS as the streaming server and VLC player on the client side to play the stream. My client machine has an onboard NIC and one mulitple (4 interfaces) interface card.
Iam using Wireshark on the client to view the RTP streams. I have changed VLC to take an IP address from the user and run the stream through the particular interface associated with the IP address given as input.
Just to check if it really is streaming through the interface I want, I run wireshark on that interface.
When I run two vlc streams through different interfaces, it sometimes streams through the appropriate interfaces and sometimes not. It just picks another interface itself and streams through that regardless of what I gave as input in VLC. On the server side the DSS shows me that its connected to the correct IP address, which is not what wireshark displays ... I tried tcpDump too but same abnormal behavior.
Is there any known problem like this ? Any pointers to what might be the problem ? Sorry for the long story ...

---

