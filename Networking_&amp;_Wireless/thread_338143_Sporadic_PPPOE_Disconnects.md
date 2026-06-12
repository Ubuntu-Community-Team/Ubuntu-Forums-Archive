---
title: "Sporadic PPPOE Disconnects"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Disguise on 2007-01-14
Hello, this is my first post here but I'm in desperate need of help. I've just migrated from XP to Ubuntu and for the most part, it's been great. However, I have a serious problem in that my ADSL connection keeps disconnecting every few minutes. I've done a lot of googling on this one but I can't find anything that helps. I've configured my connection using pppoeconf and when it drops, plog shows the following: 

Jan 14 15:29:30 hank-desktop pppd[3593]: LCP: timeout sending Config-Requests 
Jan 14 15:29:30 hank-desktop pppd[3593]: Connection terminated.
Jan 14 15:29:30 hank-desktop pppd[3593]: Modem hangup
Jan 14 15:29:37 hank-desktop pppd[6499]: No response to 4 echo-requests
Jan 14 15:29:37 hank-desktop pppd[6499]: Serial link appears to be disconnected.
Jan 14 15:29:37 hank-desktop pppd[6499]: Connect time 3.5 minutes.
Jan 14 15:29:37 hank-desktop pppd[6499]: Sent 8981 bytes, received 12724 bytes.

Reconnecting with pon seems to work just fine but doing this every couple of minutes is a real pain. I have a Realtek RTL8319 network card and it doesn't have any drivers, could that be the problem? I appreciate any help. Thank you all in advance.

---

### Post by StenmarC on 2007-01-29
I have the same problem :(

---

### Post by ayed on 2007-01-29
ME TOO! I have the same problem but it seems no one knows how to solve it, I can reconnect using the poff and pon, but I need to keep doing it every so and so! Someone please helP!!:confused: :(

---

### Post by rup on 2007-03-04
Open /etc/ppp/options file and edit the lines to read 

noauth
lcp-echo-interval 0
lcp-echo-failure 0

---

### Post by e_sela on 2007-03-04
I have the same problem.
There are many posts on the internet with this problem, but untill now, no solution.
On windows, though, the connection doesn't disconnect for weeks.

---

### Post by e_sela on 2007-03-04
I attach log messages:
Connecting (Works OK):

Mar  4 20:39:14 eitanse-desktop pppd[7125]: Plugin rp-pppoe.so loaded.
Mar  4 20:39:14 eitanse-desktop pppd[7129]: pppd 2.4.4 started by root, uid 0
Mar  4 20:39:14 eitanse-desktop pppd[7129]: PPP session is 5877
Mar  4 20:39:14 eitanse-desktop pppd[7129]: Using interface ppp0
Mar  4 20:39:14 eitanse-desktop pppd[7129]: Connect: ppp0 <--> eth0
Mar  4 20:39:15 eitanse-desktop pppd[7129]: PAP authentication succeeded
Mar  4 20:39:15 eitanse-desktop pppd[7129]: peer from calling number 00:30:88:02:DD:1D authorized
Mar  4 20:39:15 eitanse-desktop pppd[7129]: replacing old default route to eth0 [10.0.0.138]
Mar  4 20:39:15 eitanse-desktop pppd[7129]: Cannot determine ethernet address for proxy ARP
Mar  4 20:39:15 eitanse-desktop pppd[7129]: local  IP address xx.xxx.xx.xxx
Mar  4 20:39:15 eitanse-desktop pppd[7129]: remote IP address xxx.xxx.xx.xxx
Mar  4 20:39:15 eitanse-desktop pppd[7129]: primary   DNS address xxx.xxx.xxx.xx
Mar  4 20:39:15 eitanse-desktop pppd[7129]: secondary DNS address xx.xx.xx.xxx

In the moment pppoe disconnects:

Mar  4 20:54:18 eitanse-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.138 port 67
Mar  4 20:54:18 eitanse-desktop dhclient: DHCPACK from 10.0.0.138
Mar  4 20:54:18 eitanse-desktop dhclient: bound to 10.0.0.2 -- renewal in 1394 seconds.

Can someone advice why is it happaning?

---

