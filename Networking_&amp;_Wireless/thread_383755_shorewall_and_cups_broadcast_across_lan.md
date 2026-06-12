---
title: "shorewall and cups broadcast across lan"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by rosslaird on 2007-03-13
I recently installed shorewall, which sent me back a few years in terms of the cryptic nature of its configuration. I can remember when cups was like this: impossible to figure out unless you were already an expert.

So: my laptop, which is where I have installed shorewall, no longer picks up the broadcast from the cups server on another machine on the lan (which identifies the lan printer). So my laptop cannot print anymore. I can ssh into the machine that the printer is attached to, but I can't print directly. Shorewall is blocking the cups broadcast. I have searched and rtfm and I just don't know enough about firewalls to figure this out.

Help would be good. Here's my rules file (below). You can see where I've tried to allow the ip of the print server (102):

```
 ACCEPT   net     fw    icmp    8
ACCEPT   fw      net   icmp
ACCEPT   net     fw    tcp     ssh,www,https,smtp,pop3,pop3s,imap2,imaps,submission
ACCEPT   net     fw    udp     https
ACCEPT net:192.168.0.102       fw       tcp     ssh,www,https,smtp,pop3,imap2,imaps,submission
#ACCEPT   net:216.162.217.194     fw      tcp     munin

```

Ross

---

