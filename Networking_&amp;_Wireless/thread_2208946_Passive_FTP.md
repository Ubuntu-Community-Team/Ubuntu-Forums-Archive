---
title: "Passive FTP"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by bluestreek on 2014-03-03
I read around a lot and I am still having real trouble getting Passive FTP to work on my dedicated server. My ftp is set to port 7591 and I have port 1024 open in ip tables with ESTABLISHED, RELATED etc.

When I do 
lsmod | grep ip_nat_ftp
lsmod | grep ip_conntrack_ftp
It returns no result which I think means they are not loaded? I have modprobed both of them.

Any advice would be great! Right now it hangs at about to open data connection.

---

### Post by TheFu on 2014-03-03
Probably not useful to you, but 
**Don't use FTP.  Use sftp.**  [Here is why.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")
Firewalls are just 1 reason to use sftp, there are many others.

---

