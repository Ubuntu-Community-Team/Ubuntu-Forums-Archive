---
title: "Samba Works on internal network (LAN) , but is inccessible from WAN"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by papyromancer on 2008-09-22
I've gone through the goog and the book, but I'm having trouble getting outside network access to this samba share (local subnet access is great) there's no firewall installed (it think) on this (ubuntu) system, router is setup to DMZ to this server. I can ssh from client to server and vice versa. I try the 'echo "hello" telnet xxx.xxx.xxx.xxx 139' to the server from the client and get "telnet: Unable to connect to remote host: Connection timed out" here's my samba config --> [http://pastie.org/276812](http://pastie.org/276812) .  

Listing all iptables i see no reason that outside network access should be denied to port 139 because there are no rules in the iptables.  Does anyone have suggestions for me?

---

### Post by papyromancer on 2008-09-22
Apparently Samba ports are blocked system wide by Comcast at the request of the department of homeland security, and Comcast cannot unblock them for any client, business or residential.

I think I'm going to build an ssh tunnel from an ec2 instance.

--more to come--

---

### Post by gregphil on 2008-09-22
What protocol are you hoping to use to get past your router?  Basic Microsoft browsing only works within one sub-net, unless some other server extends it reach.  This is normally a good thing, as you don't normally want the entire world "seeing" your shares.

---

### Post by papyromancer on 2008-09-22
I'm hoping that a Mac or Ubuntu box will be able to be pointed to this box (in DMZ mode at a static ip) and mount the share... no discovery needed or wanted.

And a side note: here's the DHS advisory that Comcast was referencing:

[http://web.archive.org/web/20030810193533/http://www.nipc.gov/warnings/advisories/2003/Potential7302003.htm](http://web.archive.org/web/20030810193533/http://www.nipc.gov/warnings/advisories/2003/Potential7302003.htm)

---

