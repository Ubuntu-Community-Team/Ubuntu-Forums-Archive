---
title: "Cannot access certain ports (ie. 2001, 2002) appropriately - Help Please"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by XS_NNT on 2008-06-09
Hello everyone!

Long time lurker, first time poster.  I've looked long and hard, but I just can't find a solution to my problem.  Describing the problem is going to require giving some background information, so please forgive the length of the post.

I am using a program called Dynamips which provides emulation of networking devices (for study purposes).  When I start the program, it listens on port 7200 for configuration information (what matters for our discussion is the parameter of how many routers it emulates).  Each emulated device is accessible via telnet to the localhost, starting on port 2000 (router 1 is accessed on port 2000, router 2 on 2001, router 3 on 2002, etc).  For convenience, I use SSH tunnels into this computer to begin these services and give myself telnet access.  I have verified that in all cases, SSH tunneling is working properly.  Now, using a LAN connection with SSH tunneling, everything works properly.  I can begin the program which listens for routers via the SSH connection, and can open multiple telnet windows on the client machine and connect to the opened ports on the server (2000, 2001, etc). 

Here is where the problem begins.  When I try to perform the same task from a location over the Internet (again, using an SSH tunnel), ONLY ports 7200 and 2000 work... 2001+ do not, telnets to those ports (again, over the tunnel) are rejected.  I have verified that my SSH tunnels are working and that the ports are open and listening.


Any ideas as to why only port 2000 works and 2001/2002/2003+ do not?  I realize I could just open another SSH connection to the server and telnet to the localhost on those ports from there, but that is a less convenient solution (local resources outside the scope of this post provide greater convenience) and as I will be spending literally hundreds of hours with this software, the convenience would be *greatly* appreciated.


Thanks in advance!

Edit: This is on Ubuntu 8.04.  Had the same issue with 7.10.

---

### Post by XS_NNT on 2008-06-09
Bump

---

### Post by heatpumpcontrol on 2008-06-09
could it be that you're not configuring your ssh ports properly?

Try [this thread]("http://ubuntuforums.org/showthread.php?t=383053&highlight=terminal+sever+will") and see if the same happens while using vnc and portaputty.

---

### Post by XS_NNT on 2008-06-10
Yes, I can verify that my SSH ports are being forwarded properly.  I can even confirm that by virtue of Wireshark captures.  I am using a full version of PuTTY, what they describe for PortaPuTTY is exactly what I'm doing for PuTTY.

---

