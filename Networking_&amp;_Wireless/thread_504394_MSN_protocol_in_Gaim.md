---
title: "MSN protocol in Gaim"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Sondre Haugen on 2007-07-19
Gaim on ubuntu 7.04 connects to all my different IM protocols except from MSN.

Anyone who can help me out?

Her is the log from gaim -d:

dns: DNS query for 'messenger.hotmail.com' queued
dns: Created new DNS child 14889, there are now 1 children.
dns: Successfully sent DNS request to child 14889
dns: Got response for 'messenger.hotmail.com'
dnsquery: IP resolved for messenger.hotmail.com
proxy: Attempting connection to 65.54.239.140
proxy: Connecting to messenger.hotmail.com:1863 with no proxy
proxy: Connection in progress
proxy: Connected.
msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
msn: servconn read error, len: -1 error: Connection reset by peer
msn: Connection error from Notification server (messenger.hotmail.com): Reading error
msn: C: NS 000: OUT
msn: Connection error from Notification server (messenger.hotmail.com): Writing error
g_log: msn_session_disconnect: assertion `session->connected' failed
account: Disconnecting account 0x81460b8
connection: Disconnecting connection 0x8149bb8
msn: destroy httpconn (0x8595460)
connection: Destroying connection 0x8149bb8
util: Writing file accounts.xml to directory /home/sondre/.gaim

---

### Post by splintercellguy on 2007-07-19
I can use MSN support with Gaim just fine. Could it be a networking issue?

---

### Post by misfitpierce on 2007-07-19
Router or something could be blocking something needed for connection to MSN crap networks.... Possibility

---

### Post by granite230 on 2007-07-20
I have the same issue here. Would be really nice if someone knows how to fix this... cuz I'm clueless :(

---

### Post by kodoku on 2007-07-20
Are you guys using moblock? (It will block connections to the microsoft network).  To see if that is the problem, try going to Preferences > Account Settings for MSN > Advanced > Check Use HTTP Method

---

### Post by granite230 on 2007-07-22
> **kodoku said:**
> Are you guys using moblock? (It will block connections to the microsoft network).  To see if that is the problem, try going to Preferences > Account Settings for MSN > Advanced > Check Use HTTP Method

I don't think that's the problem because Gaim works perfectly when I plug in the network cable. This is a wireless only problem. I think it could be the router but I have no idea how to fix it.

Might work for Sondre Haugen though.

---

