---
title: "socket exception"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by sam_barker123 on 2008-03-15
Hi all,

I am tried to run a program.And it threw this exception

Unhandled Exception: System.Net.Sockets.SocketException: No such host is known
at System.Net.Dns.GetHostByName (System.String hostName) [0x00000]
  at System.Net.Dns.GetHostEntry (System.String hostNameOrAddress) [0x00000]
  
The program works fine in when I run it with mono in windows but not with mono in Ubuntu.

i dont think that its a problem with mono since i was able to run it with mono on ubuntu 2 weeks ago..
before i did an update :(

Can anybody tell me whats wrong?

---

### Post by kellemes on 2008-03-15
What program are you trying to run?

---

### Post by sam_barker123 on 2008-03-15
I am trying to start a SIP connection

---

