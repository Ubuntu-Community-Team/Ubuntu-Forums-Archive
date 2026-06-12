---
title: "ubuntu pptp disconnect after 2.5 mins"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by lonetree on 2008-01-05
Hi all,

I have recently configured a new ubuntu box based on 7.10 for my office to replace my existing 6.06. This ubuntu box is to act as a samba _PDC_ as well as a _file server_. I have remote users that needs to access this server, so I install pptp to act as a _VPN server_. 

Previously on my 6.06 I have no problem with this pptp server, users are able to connect to it and access files from the file server. However, on my newly installed 7.10, I keep getting a disconnection on windows clients from remote access, this happens everytime after 2.5 mins of connections. In fact, I had the same problem on a 7.04 few months back when I was playing with it. I did a log check on this 7.10 machine and found this messages in */var/log/messages* :

----
Jan  5 15:45:39 NEO-FS01 pppd[18137]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jan  5 15:45:39 NEO-FS01 pppd[18137]: pppd 2.4.4 started by root, uid 0
Jan  5 15:45:39 NEO-FS01 pppd[18137]: Using interface ppp0
Jan  5 15:45:39 NEO-FS01 pppd[18137]: Connect: ppp0 <--> /dev/pts/2
Jan  5 15:45:42 NEO-FS01 pppd[18137]: MPPE 128-bit stateless compression enabled
Jan  5 15:45:44 NEO-FS01 pppd[18137]: local  IP address 10.27.226.1
Jan  5 15:45:44 NEO-FS01 pppd[18137]: remote IP address 10.27.226.100
Jan  5 15:48:12 NEO-FS01 pppd[18137]: No response to 4 echo-requests
Jan  5 15:48:12 NEO-FS01 pppd[18137]: Serial link appears to be disconnected.
Jan  5 15:48:12 NEO-FS01 pppd[18137]: Connect time 2.5 minutes.
Jan  5 15:48:12 NEO-FS01 pppd[18137]: Sent 528 bytes, received 840 bytes.
Jan  5 15:48:15 NEO-FS01 pppd[18137]: Connection terminated.
Jan  5 15:48:15 NEO-FS01 pppd[18137]: Modem hangup
Jan  5 15:48:15 NEO-FS01 pppd[18137]: Exit.
---


this is the whole part of log for one connection. 


Does anyone has the same problem with me? Hope someone can point some pointer on this issue. 


Thanks in advance,

regards,

---

