---
title: "apache/php on ubuntu to msaccess database"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by edpatterson on 2009-01-29
I am assuming this is possible.

I need to query a msaccess database on a server 2003 box via a php script running on apache under Ubuntu.

It is part of a squid project I am working on. Squid has the requesting IP address, the msaccess database holds the user name associated with that address. I need to mate the two for a report.

From what I can find it appears that ODBC connections only work locally, not across the network.

Ed

---

### Post by cmnorton on 2009-02-14
That's not so from Windows to Linux. I'd poke further into an ODBC API document, or find some PHP sample code. There's tons of it out there. You won't care as much about specifically touching an Access DB as much as finding a network example.

---

