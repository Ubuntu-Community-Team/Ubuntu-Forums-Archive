---
title: "Does proftpd actually uses port 20?"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by divas on 2006-10-31
Hi,
I have some questions to ask about proftpd:
Does proftpd uses port 20? I doupt it does because of the following reasons:
1)
I have installed proftpd and used port 21 as the standard port.
I forwarded port 1717 of my router to port 21 of my pc.
In the ftp clien I use: [ftp://mydomain.org:1717](ftp://mydomain.org:1717) and my server works fine!!
Now suppose proftpd does use port 20 for data.
How this can be true, since I forward nothing on my router to port 20 of my PC?

2) If I change the default port from 21 to 69, the data port will still be 20 or not? (will it be 68?)? Actually, I did this (also forwarded port 1717 of my router to port 21) and the following happens:
When I hit [ftp://mydomain.com:1717](ftp://mydomain.com:1717) I log in and the client does not respond (it does not show the contents of my home ftp dir). This now seems to be a problem with the data port.
Summing up:
a) How can my server work since I don't forward port 20?
b) How do I configure the data port in proftpd?

Many thanks in advance!

---

### Post by divas on 2006-10-31
No I found out one more thing:
If I enable only port 21 on firestarter, still my server works fine, meaning that port 20 is not used. (if I am not wrong, all ports are disabled by default, except those manually defined in firestarter).

HOW CAN PORT 20 BE USED????

---

