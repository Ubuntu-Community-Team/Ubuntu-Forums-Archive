---
title: "Samba Setup, File Transfer Question"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by ortuno2k on 2010-01-11
Hello,

I'm a new Ubuntu user, been reading lots of posts from the forums and other sites online, but this particular problem I cannot find.
I setup Samba and followed a simple tutorial on how to configure it. I'm using the default smb.conf file (made a copy of the original), and shared my home folder, with write access. The only modification I made to the smb.conf file is added this line, as suggested by some info that I've read:

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

Restarted the smb services after these changes, and was able to connect to my Home folder from my Mac, using smb://myname@mysrv

The server is running on 9.10 with the latest updates, 1.5 GB RAM, XP 2500 CPU, and an Intel Gigabit NIC that I purchased a few days ago. The hard drive is a brand new WD 1TB Green. I plan to use it as a file/backup server for home use.

I can connect and see files, make folders, and other stuff, HOWEVER, my biggest problem comes when copying data over to it...

I tried copying a large folder containing 1.48 GB of data from my Mac to the server, both hard-wired using the Gigabit connection. It took exactly 2 min 22 secs for the transfer to complete, and the copy-file progress window kept pausing every few seconds, and every few hundred MBs.

Example: it copies 170 MB, then it pauses for a few seconds...it copies a few other hundred MB, and pauses again, and again, until it's finished. The data is copied successfully, but this is very weird. I'm not even sure how to calculate my network speed like this, or where the problem could be.

I consider myself computer literate and somewhat techie, but have no experience with Ubuntu nor the terminal, so I have to "Google" pretty much every other task that I want to achieve on my server.

Can someone please guide me on the right direction?

---

### Post by cariboo on 2010-01-11
To check internal network speed, I use iperf, it is in the repositories. There are also mac and windows versions available.

Set up one computer as the server by issuing the follow command:

```
iperf -s
```

then on another system on the network run:

```
iperf -c <servername>
```

where <servername> is the name or ip address of the computer that the iperf server is running on. 

I get the following result on my 100Mbps network:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 58248 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.5 Mbits/sec
```

In the above case the name of my file server is willy.

---

### Post by ortuno2k on 2010-01-11
Thanks. I've used the tool and noticed that I'm only getting about 280 mbps out of the theoretical 1 gpbs, something else must be wrong in the way. 
Gotta keep looking.
Again, thanks!

---

