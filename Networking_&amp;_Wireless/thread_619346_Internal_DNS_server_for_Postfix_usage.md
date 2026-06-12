---
title: "Internal DNS server for Postfix usage"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Berobero on 2007-11-21
Hello,

I am using postfix mta in the office on Ubuntu server. From outside I can connect pop/smtp servers by domain name but I have a small network in the office and since the postfix server is inside the same network, I have to use some other mail accounts with IPs like 192.168.1.6 as pop/smtp servers.

Can I install and setup an internal dns server to resolve mail.xxx.com to internal IPs ? If so, how can I make it ?? Is it possible with  Bind ?

Or is there an easier  way to make it ?? :confused:

Thanks in advance

---

### Post by Blutack on 2007-11-21
Bind is your chappy, fairly easy from the looks of things
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

