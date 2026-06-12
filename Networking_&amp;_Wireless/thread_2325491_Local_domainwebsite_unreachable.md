---
title: "Local domain/website unreachable"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by walttheboss on 2016-05-23
I have a local apache2 and Concrete5 driven website.  [https://www.msgkmg.com](https://www.msgkmg.com)
If I have an entry in /etc/hosts 192.168.2.XXX [www.msgkmg.com](www.msgkmg.com) I can hit the site fine from any pc on the lan
If I am at home (off-site) I can hit the site fine.

PROBLEM:  If I delete the entry in hosts and try to get to the website from a computer on the lan it will never resolve.
Traceroute goes nowhere.  It should leave the building looking for a DNS entry.  Finding it then it should come back in through the router to the server.

it never works. HELP

Kubuntu 14.04 updated.
Asus RT-N66W running the latest merlin software.

---

### Post by walttheboss on 2016-05-31
> **walttheboss said:**
> I have a local apache2 and Concrete5 driven website.  [https://www.msgkmg.com](https://www.msgkmg.com)
If I have an entry in /etc/hosts 192.168.2.XXX [www.msgkmg.com]("http://www.msgkmg.com") I can hit the site fine from any pc on the lan
If I am at home (off-site) I can hit the site fine.

PROBLEM:  If I delete the entry in hosts and try to get to the website from a computer on the lan it will never resolve.
Traceroute goes nowhere.  It should leave the building looking for a DNS entry.  Finding it then it should come back in through the router to the server.

it never works. HELP

Kubuntu 14.04 updated.
Asus RT-N66W running the latest merlin software.


SOLVED:  Someone had put some dns scripts into my router.  A factory reset of the router solved the issue.

---

