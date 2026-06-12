---
title: "Raw Socket Programming in C."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by open_source_sux on 2009-01-27
I am trying to write a TCP/IP program using raw sockets.  I construct the IP header and call setsockopt with IP_HDRINCL so ubuntu doesn't insert it's own ip header in for me when I run my C/C++ program.  I also installed wireshark to see if my program works.  I always see "bogus tcp header must be at least 20 bytes in length" error when i send my custom TCP packet and it appears all the TCP fields are zeroed out.  The IP header (except for tcpheader) seems fine.  Any reason for this? I'm suspecting that Ubuntu might be doing something like windows where it messes with your raw sockets and network traffic.

---

### Post by Redache on 2009-01-29
I'd try asking in the Programming Forum as they're better suited to help you.

---

