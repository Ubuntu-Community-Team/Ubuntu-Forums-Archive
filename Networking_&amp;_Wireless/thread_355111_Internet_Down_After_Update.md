---
title: "Internet Down After Update"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by linuxNewb on 2007-02-06
A couple of days ago I updated I don'y know what packages they were. Now I can not connect to the interent. Instead of a 72. IP address I am now getting a 169 IP address.

Is there a way to roll back the last update (all packages)?

---

### Post by gradedcheese on 2007-02-06
The package log is at /var/log/dpkg.log in case you want to see what you updated last.

How do you normally get your IP address?  Static IP or DHCP?  169. usually implies a link-local address, depending on the next byte anyway.  I'm guessing you previously had a static IP address?  If so, assuming that your network card is eth0, try:

sudo ifconfig eth0 72.xx.xx.xx up

(substitute your IP address there)

---

