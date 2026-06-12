---
title: "Update Ubuntu 12.04 to 13.10: vdr/streamdev not working over network"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by Data on 2014-01-11
Hi there,

I just updated my (TV) server from 12.04 LTS to 13.10.

I had vdr with streamdev-server running fine on it. Now, that only works locally. svdrphosts.conf and streamdevhosts.conf are setup and appear correct.

Strange thing is, that the communication between the client and the server starts, they exchange packages, but then the client does not receive any packages more.

Looking at tcpdump, both sides show (server 192.168.02, client 192.168.0.3):
13:43:33.852204 IP 192.168.0.3.58211 > 192.168.0.2.3000: Flags [ S], seq 4039666280, win 29200, options [mss 1460,sackOK,TS val 315973 ecr 0,nop,wscale 7], length 0
13:43:33.854508 IP 192.168.0.2.3000 > 192.168.0.3.58211: Flags [S.], seq 1059981805, ack 4039666281, win 28960, options [mss 1460,sackOK,TS val 20114770 ecr 315973,nop,wscale 7], length 0
13:43:33.854548 IP 192.168.0.3.58211 > 192.168.0.2.3000: Flags [.], ack 1, win 229, options [nop,nop,TS val 315974 ecr 20114770], length 0
13:43:33.854751 IP 192.168.0.3.58211 > 192.168.0.2.3000: Flags [P.], seq 1:108, ack 1, win 229, options [nop,nop,TS val 315974 ecr 20114770], length 107
13:43:33.856615 IP 192.168.0.2.3000 > 192.168.0.3.58211: Flags [.], ack 108, win 227, options [nop,nop,TS val 20114770 ecr 315974], length 0

After that, only the server tries to send packages, but the client does not receive anything:
13:43:33.754086 IP 192.168.0.2.3000 > 192.168.0.3.58211: Flags [P.], seq 1:145, ack 108, win 227, options [nop,nop,TS val 20114771 ecr 315974], length 144
etc.

Communication on the server itself works fine and delivers a decent TS file.

Has anybody an idea about that? Or in which direction I should search?

Michael

---

### Post by Data on 2014-01-12
Ok, let's make it simpler:

Has anybody vdr with streamdev running under 13.10?

Michael

---

