---
title: "New Syslog server setup (10.4)"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by sephiorth on 2010-10-19
Hi,
I've found the following three guides on how to set this up:
[http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml](http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml)
[http://johncrackernet.blogspot.com/2008/09/howto-setup-syslog-server-in-ubuntu.html](http://johncrackernet.blogspot.com/2008/09/howto-setup-syslog-server-in-ubuntu.html)
[http://www.aboutdebian.com/syslog.htm](http://www.aboutdebian.com/syslog.htm)

These seem alright. But I did a barebones install of Ubuntu server and can't find any syslog.conf files (using whereis and scanning /etc) and the only installer I found was syslog-ng via "sudo apt-get install syslog-ng"

I just want to get rolling with this, i need to start backing up four servers' logs into one centralized server.
Any advice would be greaaaaaaaaaat

---

### Post by M!K3_$ on 2010-10-20
by the looks of it, you need to make a syslog.conf file.

---

