---
title: "Internet services (ftp, http, telnet)"
date: 2004-12-13
forum: Networking &amp; Wireless
---

### Post by psychomonkey on 2004-12-13
Hello,

I'm pretty new to Linux in general (I've installed a few, but the commands are a little hazzy) but have found Ubuntu to be very easy to learn. My issue is this: How to you set web services like ftp, http and telnet to a system running Ubuntu? Can anyone tell me or at least point me to the documentation? 

Thanks in advance

---

### Post by Ken_Lewis81 on 2007-05-15
There are good resources at [https://wiki.ubuntu.com](https://wiki.ubuntu.com), detailing a lot of what people have been doing with Ubuntu.  You don't want to use Telnet ever again, as it transmits your passwords as plain text -- [SSH](https://help.ubuntu.com/community/SSHHowto) is the standard for Secure SHell access.  HTTP is served by Apache, and the combination of Linux kernel, Apache web server, MySQL database and PHP scripting is know as LAMP, and covered at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).  FTP serving is at: [https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer).

I hope that this community-driven documentation helps.
Take care.
Ken.

---

