---
title: "Network seemingly functional, but browsing impossible"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by aloscha on 2008-10-19
Hi.

I installd Kubuntu on my Fujitsu Esprimo V5535 laptop yesterday and tried to get drivers. With a bit of luck, I found drivers for my Ethernet card and it seemed to be working at first, until I tried to actually get a web page. Then Konqueror just tells me that it's waiting for reply, until server times out. Pinging hosts is possible, but the response time is a lot longer than it should be. Traceroute works, but response times are ridiculously slow (hundreds of milliseconds just for my router to respond). Since I'm a complete newbie at Kubuntu, I don't have a clue what the problem could be. My other computer works perfectly. Any help is appreciated.

---

### Post by superprash2003 on 2008-10-19
you could try changing your DNS servers to opendns.Their ips are 208.67.222.222 qand 208.67.220.220
For reference : [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by aloscha on 2008-10-19
> **superprash2003 said:**
> you could try changing your DNS servers to opendns.Their ips are 208.67.222.222 qand 208.67.220.220
For reference : [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Unfortunaly that didn't work. Any more suggestions?

---

### Post by superprash2003 on 2008-10-31
try changing MTU values to 1500 or 1492 or 1454

---

