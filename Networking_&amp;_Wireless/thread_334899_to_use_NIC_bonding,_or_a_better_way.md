---
title: "to use NIC bonding, or a better way?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by WEKurtz on 2007-01-09
Current setup:
Windows 2000Pro
Via C3 866Mhz
384Mb Ram
1x 40Gb PATA (20Gb OS partition, 20Gb P2P download temp area)
3x 200Gb PATA (storage; media, backups, install images etc)
2x 10/100 NICs (bus-mastering Dlink TX530+, if it matters. only 1 in use)
Acting as a: File server and Torrent client. VNC access only.

I'm thinking of moving to Edgy Server (gives me a DNS/DHCP/Proxy learning platform) and I frequently drag very large files to/from this machine, often concurrently to different machines. I was wondering if it's better to:

A) bond the two NICs (1 IP) and leave it at that;
B) bond the two NICs (1 IP) and add a 3rd NIC (diff. IP) for WAN traffic (torrents, etc); or
C) something else?

If 'B' is a good option, please say a few words about how to keep Samba & NFS traffic off that interface.
 Thanks.

---

