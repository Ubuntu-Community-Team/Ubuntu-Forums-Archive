---
title: "[SOLVED] Connot resolve hostnames - tried all the tips I can find"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by rpkehoe on 2008-01-26
I am not sure how this happened, but I have recently been unable to resolve hostnames.  This began intermittently, and now I can only connect to a website by entering the IP address or using TOR.

I have check the DNS setting in my network config, and they are correct.  I have all the records for my ISP, as well as my router IP, but no beans.

I do have dhcp3-client and common installed (which I also tried re-installing).  The only significant change I have made to my system was to install KDE4, but it has since been removed.

Help is greatly appreciated

---

### Post by kevdog on 2008-01-26
Can you post

cat /etc/resolv.conf

---

### Post by rpkehoe on 2008-01-26
$ cat /etc/resolv.conf
search carolina.rr.com
nameserver 216.181.31.11
nameserver 216.181.30.11
nameserver 192.168.0.1
nameserver 24.25.5.149

---

### Post by kevdog on 2008-01-26
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by rpkehoe on 2008-01-26
Thanks, OpenDNS did the trick

---

### Post by kevdog on 2008-01-26
Glad it worked for you.  Could you mark the thread as solved?

---

