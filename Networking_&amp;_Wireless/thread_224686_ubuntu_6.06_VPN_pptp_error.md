---
title: "ubuntu 6.06 VPN pptp error"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by titovn on 2006-07-28
Hello!!!

checho@ubuntu:/etc$ sudo pptp-command start
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 10.10.0.161
remote IP address 83.228.79.252
couldn't open lock file: No such file or 
directory at /usr/sbin/pptp-command line 793.

What can i do?
Somebody help me!

---

### Post by titovn on 2006-07-28
Line 793:
open(LOCK, ">>$subsys_dir/pptp") or die "coud\ldn't open lock file: $!";

---

### Post by titovn on 2006-08-02
mkdir /var/lock/subsys

---

