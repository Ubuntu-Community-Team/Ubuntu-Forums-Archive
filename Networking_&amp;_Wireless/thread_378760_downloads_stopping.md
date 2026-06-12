---
title: "downloads stopping"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by jkearney on 2007-03-07
Hi there,

I am new to ubuntu, and was wondering if anyone could help me with my first (of hopefully few!) problems...

I do not have a problem with connectivity, ping'ing anyaddress.com results in 100% responses.

However, two files in my snaptics update manager will not download and install, since they always get to about 75% of the way through and then just stop permanently.

This also seems to happen with other downloads, i recently did a:
```

sudo apt-get install libc6-dev

```

and had to do this a number of times to get it to install, since each time it would download about 80% of the file and then just stop.... and wait... and wait...

since i can surf fine / ping fine etc - i was wondering if any of you chaps could help me establish exactly what the problem is?

Thanks very much

James Kearney

(running Linux kkint 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux)

---

### Post by Mr. C. on 2007-03-07
Ping is a very short packet, requiring no TCP connection.  This can only be used to diagnose basic connectivity.   It cannot be used to indicate network health, or ferret out other problems.  Like asking if someone's alive... they certainly cannot say No, but no response doesn't mean dead either!

Web browsing requires many short term connections; this also is not the best metric of health.

Aborted or hung downloads indicate something more problematic; like long hangs and connection issues.  It can also be caused by several other factors.  TCP/IP networking is very robust, and works around these problems in most all cases.

The root cause of the issue you see is difficult to diagnose without more data and investigation.  Start with the basics by giving a description of your network setup, networking hardware, etc.  After that, we can checking the health of your network connection, traceroutes to destinations where the trouble occurs (while the trouble is occurring).

MrC

---

### Post by jkearney on 2007-03-14
ok well it is an ubuntu server, on virgin broadband, sitting behind a router.

When the trouble occurs i will traceroute to the host ip and paste it here!

thanks for the help,

James

---

