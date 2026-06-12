---
title: "Problem with ISDN dial-in"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by digitalshadow on 2007-01-29
Hello,

Following situation:
a server running ubuntu, with isdn card installed and configured using isdnutils
a cisco ISDN router in the network connected to the server over an ISDN line

the ISDN interface on the server is up, and it seems to be able to dial out. Now i try to ping the server from the cisco decive using the ISDN line. I can see incoming calls in /var/log/messages, but not a single ping packet returns. When i capture packets on ippp0 (my ISDN interface), i don't see no packets arriving or leaving. I even can't see packets on ippp0 when i dial OUT. /var/log/messages shows that i'm dialing. even the cisco device gets the incoming call, but i don't get connected. How can there be no packets on ippp0?

An incoming call looks like this (/var/log/messages):

Jan 29 08:12:38 ubuntu01 kernel: [17181354.040000] isdn_net: call from <REMOTE NUMBER>,7,0 -> <LOCAL MSN>
Jan 29 08:12:38 ubuntu01 ipppd[5973]: Local number: <LOCAL MSN>, Remote number: <REMOTE NUMBER>, Type: incoming
Jan 29 08:12:38 ubuntu01 ipppd[5973]: PHASE_WAIT -> PHASE_ESTABLISHED, ifunit: 0, linkunit: 0, fd: 8
Jan 29 08:12:38 ubuntu01 kernel: [17181354.208000] isdn_net: ippp0 connected
Jan 29 08:12:38 ubuntu01 ipppd[5973]: Modem hangup
Jan 29 08:12:38 ubuntu01 ipppd[5973]: Connection terminated.
Jan 29 08:12:38 ubuntu01 ipppd[5973]: taking down PHASE_DEAD link 0, linkunit: 0
Jan 29 08:12:38 ubuntu01 ipppd[5973]: closing fd 8 from unit 0
Jan 29 08:12:38 ubuntu01 ipppd[5973]: link 0 closed , linkunit: 0
Jan 29 08:12:38 ubuntu01 ipppd[5973]: reinit_unit: 0
Jan 29 08:12:38 ubuntu01 ipppd[5973]: Connect[0]: /dev/ippp0, fd: 8
Jan 29 08:12:38 ubuntu01 kernel: [17181354.628000] ippp0: remote hangup
Jan 29 08:12:38 ubuntu01 kernel: [17181354.628000] ippp0: Chargesum is 0

An outgoing call:

Jan 29 08:13:29 ubuntu01 kernel: [17181405.448000] ippp0: dialing 1 <REMOTE NUMBER>...
Jan 29 08:13:30 ubuntu01 ipppd[5973]: Local number: <LOCAL MSN>, Remote number: <REMOTE NUMER>, Type: outgoing
Jan 29 08:13:30 ubuntu01 ipppd[5973]: PHASE_WAIT -> PHASE_ESTABLISHED, ifunit: 0, linkunit: 0, fd: 8
Jan 29 08:13:30 ubuntu01 kernel: [17181406.236000] isdn_net: ippp0 connected
Jan 29 08:13:30 ubuntu01 ipppd[5973]: Modem hangup
Jan 29 08:13:30 ubuntu01 ipppd[5973]: Connection terminated.
Jan 29 08:13:30 ubuntu01 ipppd[5973]: taking down PHASE_DEAD link 0, linkunit: 0
Jan 29 08:13:30 ubuntu01 ipppd[5973]: closing fd 8 from unit 0
Jan 29 08:13:30 ubuntu01 ipppd[5973]: link 0 closed , linkunit: 0
Jan 29 08:13:30 ubuntu01 ipppd[5973]: reinit_unit: 0
Jan 29 08:13:30 ubuntu01 ipppd[5973]: Connect[0]: /dev/ippp0, fd: 8
Jan 29 08:13:30 ubuntu01 kernel: [17181406.564000] ippp0: remote hangup
Jan 29 08:13:30 ubuntu01 kernel: [17181406.564000] ippp0: Chargesum is 0

(i've overwritten the local and remote numbers, because their're internal company numbers that i can't post here)

iptables are empty with policy ACCEPT, i really can't imagine where the packets get lost.

Any ideas?

---

