---
title: "&quot;TCP Out-of-Order&quot; Errors"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by boomcat on 2008-01-16
I have all of my music on a headless Ubuntu server. I play the music on a Ubuntu laptop client over a wireless 802.11g network using the NFS system. The music player I use on the laptop is Rhythmbox. The problem is that the music sometimes stops. It may be silent for anywhere from 10 seconds to five minutes before resuming.

I put a packet sniffer on the case using a Windows laptop, and I am seeing hundreds of repeated frames. A typical entry is:

Frame: 36339
Time: 186.47916
Source: 192.168.2.102
Destination: 192.168.2.104
Protocol: NFS
Info: [RPC retransmission of #36338][TCP Out-of-order] V3 GETATTR Call FH:0xd92f2756

Any advice on trouble-shooting this?

---

