---
title: "[SOLVED] &amp;quot;nmap localhost&amp;quot; - server is down ?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by LinuX-M@n1@k on 2008-04-03
When I run "nmap localhost", it says that the host is down...
```
boris@linux:~$ nmap localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2008-04-03 13:04 EEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.007 seconds
boris@linux:~$
```
Any ideas why ? I've stopped iptables ( iptables -F ), rebooted and nothing...

---

### Post by LinuX-M@n1@k on 2008-04-03
*bump*

---

### Post by equity on 2008-04-03
Maybe you shut down localhost?
Have you tried to bring it up by typing "sudo ifconfig lo up"?

---

### Post by LinuX-M@n1@k on 2008-04-03
yep, that was the problem :) solved

---

