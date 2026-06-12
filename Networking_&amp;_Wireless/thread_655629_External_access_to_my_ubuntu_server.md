---
title: "External access to my ubuntu server"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by rkehn on 2008-01-01
Quick review:
I have two ubuntu servers, 1 @ 6.10 and 1 @ 7.10
The 6.10 is accessible from outside my network (www,ftp,ssh,...) and every thing works as expected.

Now on my fresh install of 7.10 LAMP, openSSH, and mail. Things seem to fall apart.

I understand port forwarding the router etc...
All machines are static ips...
Do have outgoing access to net (tested via apt-get to get webmin)

I port forward my ssh to some port to something like 3122.

If I connect from inside the network via 192.168.1.55:3122 were all good.

If I connect from inside the network using my comcast external IP like myhouse.tzo.com:3122 it times out.

So, ok I start doing the normal troubleshooting and end up running tcpdump on the 7.10 machine which shows me that the original SYN packet come in but to syn/ack goes out.

Since the SYN is making it to the computer I believe the router is not to blame. I know the SSH is running and lisening to the port cause I can hit it with the 192.168...:3122 which works fine.

Please note that this a fresh install of ubuntu 7.10 and I have made to changes to the firewall.

Any help would be greatly appreciated!

-R

---

### Post by rkehn on 2008-01-10
Replaced the router and everything is fine now. :)

-R

---

