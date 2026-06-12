---
title: "Gutsy: Torrent enabled by FW yet rejected?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by mibadt on 2007-10-25
Hi,
I'm on a Kubuntu Gusty PC (fresh install) on a LAN which contains an ADSL modem/router. The Gutsy runs guarddog FW and Ktorrent configured (due to security consideration) to use "custom" ports both for tracker (UDP) and torrents (TCP). Naturally, I've added custom "rules" both to the router and the FW (both zones-local and Internet) to open and forward these ports.
However, my syslog (which grows fast..) indicates multiple TCP packets sent to the torrent port are rejected (yet Ktorrents works, although, probably, not at full throttle).

Can somebody help me?

Thanks

Michael Badt


-----copy of 1 abort message from syslog (port number replaced by $$$$$$)---
Oct 25 16:13:16 Miki-Desk kernel: [38698.500000] ABORTED IN=eth0 OUT= MAC=00:14:85:18:62:ee:00:30:0a:2a:d2:f7:08:00 SRC=87.194.98.61 DST=10.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=28631 PROTO=TCP SPT=56463 DPT=$$$$$$ SEQ=1828022187 ACK=1828022187 WINDOW=0 RES=0x00 RST URGP=0

----------------------------------------------------------------------------------

---

### Post by fain on 2007-10-25
Ive tried using a torrent with firestarter and it always chooses a random port to connect. so i just disable my firewall till my torrent gets done then re-enable it as i have no clue what port its going to connect on. I think its just the incoming connections thats random. I haven't fiddled with it very much. My server is not very mission critical so i can do this without too much worry.

---

### Post by mibadt on 2007-10-25
Thanks, but I' rather leave my FW permanently on.


Anybody else?

Michael Badt

---

### Post by fain on 2007-10-25
I totally agree and i would like to know a solution too. I just don't have time to research it with school, work and all.

---

