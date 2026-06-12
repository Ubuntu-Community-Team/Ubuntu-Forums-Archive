---
title: "Lost All Win95 connections to Samba"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by dgermann on 2006-08-03
Hi--

Last night I shut down my network for the thunderstorms going through the area, and unplugged it all. When I booted up this morning, I had no Win95 connection to my samba server.

My setup: Ubuntu 6.06 server, running samba 3.0.22. 3 Ubuntu workstations, 1 WinXP Pro, 2 Win95 boxes. The Ubuntu boxes mount the same directories as the Win boxes, using cifs.

What I have tried: checking log files in /var/log/samba--nothing even seems to mention login attempts by either Win95 station. Same for syslog and /var/log/messages.

The server and the two win95 boxes can ping each other. One Win95 box can be accessed via vnc. Two of the Win boxes can ping google.com (the one that cannot rarely uses an internet connection, so I might not have changed things around on it when I got my router a while back). So the network connections are working.

Rebooted the server. Rebooted one of the Win95 boxes multiple times.

Tried mapping drive letters to the server. Got this: the network name is either incorrect or on a network to which you do not have full access.

I am able to login to the server directly and through other connections, one of which is an Ubuntu workstation, using the same login name. So the user and password is working.

The WinXP box has had no trouble accessing the samba files, opening, reading, editing, saving. All is normal.

The Win95 boxes allow me to login to the particular W95 computer, but then when the screen comes up about logging in to samba, it says a connection cannot be found.

I have made no changes in any box (Oh!--except I did do the updated files that came up on Update Manager on my Ubuntu workstation this morning--nothing on any other box) since last night. It is unlikely that I have done anything on the server since the last time I rebooted it--but it is not impossible.

So how would you go about trouble shooting this? The two Win95 boxes are at the moment essential to us, in our production environment.

Thanks!

---

### Post by dtfinch on 2006-08-04
I haven't used win95 in probably 8 years. The cause is probably some name resolution problem that shouldn't be ignored, but as a quick fix you might try creating a file called "lmhosts" (no file extension) in your windows directory, where you can specify the name and ip address of the samba server, assuming the ip is static. There should be a sample file called lmhosts.sam which you can use for reference.

---

### Post by dgermann on 2006-08-04
dtfinch--

Thanks!

Already have a hosts. and lmhosts. file on each Win95 machine--have had for years. Will recheck the entries there now.

....

OK, checked. Both of those files have the right entries for the server, and a ping of the server name shows that it is using the right ipaddress.

Why would the names have changed overnight?

I am wondering if the switch may have gone bad.

I have been having trouble connecting to pop.compuserve.com for the last couple of weeks. I have tested it via telnet and cannot connect reliably there (connect about 1 time in 15)--can connect via telnet to other POP mail servers, such as yahoo and comcast. I took the router out of the mix a couple days ago and was able to connect to Compuserve readily and reliably. But at the same time I took the router out of the loop, I also bypassed the switch.

How would I check this out? Could I take the switch to a dealer and have them test it?

Thanks, dtfinch!

---

