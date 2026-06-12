---
title: "File transfer speed with netatalk"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by MrGando on 2008-04-16
hi guys, I have a home server with 3 OSX computers ( INtel Macs ) and my ubuntu box, I installed netatalk about a year ago and the download speed ( transfering files from the ubuntu box to ANY of the other macs ) was VERY slow.

I did some research and this is NOT netatalks fault, is OSX fault, to fix it , you can try this command line command as SUDO on the CLIENT side. ( Mac OSX side) 

sysctl -w net.inet.tcp.delayed_ack=2

You will notice the difference.

Cya around, and hope it helps someone :)

---

