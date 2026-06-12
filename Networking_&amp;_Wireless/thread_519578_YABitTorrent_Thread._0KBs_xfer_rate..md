---
title: "YABitTorrent Thread. 0KB/s xfer rate."
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Larsen on 2007-08-07
Distro: 6.06LTS
Client: Default Gnome.bittorrent
Equipment I-Burst broadband modem connected via Ethernet.
Dialer : RoaringPenguin-PPPoE
Firewall: 0xHardware 1xSoftware(IPTables+Firestarter)

Firewall Configuration via firestarter
Restrictive by default.
Port 80 (HTTP) Allow outbound and replies.
Port 443(HTTPS) Allow outbound and replies.
Port 6881-6889 (Bittorrent) Allow Outbound and Inbound(both replies and connections).

Behaviour of client.

Msg:Establishing connection to peers.

Following entries appear in Firewall log
```

BLOCKED CONNECTIONS
out ppp0 48463 81-233-240-209-no50.tcbn.telia.com 44bytes TCP 0x00(TOS)
+ additional entries all 44 bytes to similar style names on ports 
9090
21247
32760
45380
61000

all outbound.
each repeated once after a wait of 2 to 3 seconds.

```
No further entries in firewall log.
Download rate 0KB/s
Upload Rate 0KB/s

Do I have a trojan in the Bit torrent client?
Or is something else going on here?

I attempted disabling Bit-torrent in the firewall  and I got outgoing hits on ports 6881 and 6882 as expected but also on port 9090?? So the bt.client is sending on ports 6881 and 6882 but nothing is happening.

Any advice appreciated, if you need more data, let me know.

Larsen

---

### Post by Larsen on 2007-08-08
Update:

Ktorrent tried. Gives a lot more info.
Same hits noted in firewall.

Tried setting outgoing connections to "permisive by default".

Improvement
Trying new torrent file in Ktorrent. selected one because it had 83 seeders and only 10 peers at the time so it seemed a good test candidate.

Ktorrent now establishes connections, 
Ktorrent obtains file availability just fine.

BUT Initially each connection reads as choked, then about a minute later changes to snubbed.
Ktorrent keeps trying new connections over time but with the same result. 

Download speed still 0KB/s

So once again, any ideas anyone.

Larsen

---

