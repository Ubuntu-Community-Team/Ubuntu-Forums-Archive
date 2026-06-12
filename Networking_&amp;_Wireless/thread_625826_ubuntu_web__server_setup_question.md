---
title: "ubuntu web  server setup question"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2007-11-28
Hi all,

I have run an apache web server for many years on an old Pentium 2 running Debian 4.  I'm putting a new system into production to replace it and want to use Ubuntu as the OS.  I have set up the server following the easy-as-pie video at [http://www.lullabot.com/videocast/install-local-web-server-ubuntu](http://www.lullabot.com/videocast/install-local-web-server-ubuntu).

I have copied over my config for my old server and tweaked it so the site roots point to their new respective locations, set up an FTP service, VNC, etc.  The sites all work great when tested locally and by other systems on the local network.  I have the server set up with a manual IP address of 192.168.0.100 and have all the port forwarding allowances on my DSL router to direct requests to this address (ports 80, 21, 5900, etc).  Again, locally and within the local private network all these services work great.  However I'm unable to get any of these services to function outside the private network.  When I hit my sites, attempt to VNC in, FTP, or whatever it seems that I connect to the server but the server does not respond.  With a web browser I get a "connection timed out" response after hanging for a while.  VNC does about the same, hangs for about 15 seconds then errors with "failed to connect to server".  FTP, again "connection timed out".

I've triple checked my port forwardings on my router and am sure they're right.  Same router that I used with my old server for years.  And the services are running and look great locally.  Is there something I could be missing here?  thanks for any help you can provide.

---

### Post by mrtrick on 2007-11-28
Firewall on the box? hosts.allow / deny access lists?

---

### Post by wendallsan on 2007-12-03
Would giving my hosts.allow a line of ALL : ALL work?  Assuming I have a hardware firewall in place so I don't need to run a firewall on the local system?

also, is there a firewall on an Ubuntu system out-of-the-box other than IPTABLES listings?

thanks!

---

### Post by wendallsan on 2007-12-03
Let me correct my above question, since I already found one mistake in my systax:

ALL: ALL: ALLOW

That would allow access to this box from any IP address?

---

