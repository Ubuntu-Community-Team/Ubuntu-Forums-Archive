---
title: "Cannot Assign Requested Address in Terminal IRC Apps"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by jpyper on 2007-10-21
***_irssi Output:_***
22:02 -!- Irssi: Looking up chat.freenode.net
22:02 -!- Irssi: Connecting to chat.freenode.net [140.211.166.3] port 6667
22:02 -!- Irssi: Unable to connect server chat.freenode.net port 6667 [Cannot 
          assign requested address: 82.96.64.4]

***_ScrollZ Output:_***
[S+Z] Connecting to port 6667 of server chat.freenode.net
[S+Z] Unable to connect to port 6667 of server chat.freenode.net: socket:
      Cannot assign requested address

***_BitchX Output:_***
-:- BitchX: Auto Response is set to - john
-:- Connecting to port 6667 of server irc.ubuntu.com [refnum 0]
-:- Unable to connect to port 6667 of server irc.ubuntu.com: Cannot assign
          requested address

***_ircII Output:_***
*** Connecting to port 6667 of server chat.freenode.net
*** Unable to connect to port 6667 of server chat.freenode.net: Unknown host


GUI IRC clients work fine. I'm using Konversation and X-Chat with no problems. I'd much rather use a terminal client like irssi though.

Any ideas what might be causing my "cannot assign requested address" problem?

I'm running Gutsy, upgraded from Feisty. I run pdnsd as a local caching DNS server. I've disabled pdnsd and used both the DNS servers from Comcast (my ISP) and both servers from OpenDNS.com. To no avail.

---

