---
title: "Ubuntu server constantly dropping packets"
date: 2018-09-05
forum: Networking &amp; Wireless
---

### Post by bav2 on 2018-09-05
About 5 years ago I built a small Ubuntu server for my network that has most movies and music on it so I can stream it to my other computers/TV on the network. Everything was working fine but we had to change routers a while ago (TP-LINK Archer C9) and now we are getting poor performance over the network. I can connect to the server just fine and file transfer is fast, 1Gbps, but it keeps dropping packets and slowing down mid-transfer.

For example, during some movie playback, it will play about 10-15 seconds just fine then freeze for a couple seconds before resuming. When I ping the server from my desktop over the network I get a constant <1ms time then it will hang for a second and I get a "request timed out". Nothing on the machine running the Ubuntu server has changed, it was its own static IP.

My knowledge is limited when it comes to networking so I don't know how to troubleshoot this problem. Any help would be appreciated.

---

### Post by TheFu on 2018-09-06
I would make a grid and fill in the server, clients and how those clients access the server.  Then I'd look for which clients show problems and look for a "common cause" between all the clients with issues.

Of course, checking the log files for all the systems and the router(s) would be important too. Look for disk controller, cabling, and HDD faults.

Be systematic.
Don't skip anything.
Look at the cables, ports, NICs, and if wifi is used, look at the different locations. Wifi can be interfered with so easily. Avoid.
Also look at the protocols used.  DLNA is designed for streaming.  Samba is not. NFS is a middle ground, if you can use it.

If all the clients have issues, it is either the network/router/switching or the protocol or the server.

---

### Post by SeijiSensei on 2018-09-06
What are using as the streaming method?  DLNA via Plex or minidlna?  NFS file-sharing (my preference)?

---

