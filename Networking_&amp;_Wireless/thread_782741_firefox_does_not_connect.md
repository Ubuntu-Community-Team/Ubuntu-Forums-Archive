---
title: "firefox does not connect"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by hadian on 2008-05-05
i installed ubuntu 8.04 on a machine with conexant modem. firefox works fine when i connect to web with local network but then i use modem it does not work while gftp works (so the problem is not with the modem).

---

### Post by Paul Warelis on 2008-05-05
When Firefox is not working, more often than not it, it's a local resolver or DNS issue. First check your /etc/resolv.conf file to see if you're using the right nameserver.

---

### Post by superprash2003 on 2008-05-05
you could try changing your DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by hadian on 2008-05-05
the dns taken by the system in /etc/resolv.conf file are 85.185.163.5 and 85.185.163.4

i tried the command in above link which is adding the following line to /etc/dhcp3/dhclient.conf:
prepend domain-name-servers 208.67.222.222,208.67.220.220;
but nothing cganged. 
if the dns is not set correctly how does the gftp or filezilla works correctly?

---

