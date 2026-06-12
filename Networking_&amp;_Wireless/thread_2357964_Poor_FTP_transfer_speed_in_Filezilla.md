---
title: "Poor FTP transfer speed in Filezilla"
date: 2017-04-08
forum: Networking &amp; Wireless
---

### Post by usrandrd3 on 2017-04-08
I am using Ubuntu from a few months and i have one problem:
- file transfer (download/upload) via Filezilla works very,very poor (takes 1 hour to upload or download php files such as Wordpress script). Even opning a simple php file from server takes too long.
- file transfer is poor only on external countries (i am in an European country and here works super fast), but when working with US or other servers is poor
- on Windows the same fiels are transferred normally (i work with the same servers like before installing Ubuntu)
- tested on many different servers

How to debug this (i am kind a fan of Filezilla)?

thanks

---

### Post by TheFu on 2017-04-08
Test using other programs - ncftp, ftp, rsync, iperf and report the results for each.

However, really plain FTP should have died out around 1994 and shouldn't be used since.

---

