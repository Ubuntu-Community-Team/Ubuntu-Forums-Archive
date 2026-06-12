---
title: "ubuntu from xp ICS"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by Hacim on 2006-10-15
Hello,I have a Hard modem connected to my ubnutu box but my isp doesn't support v.92 so call waiting won't work.I have the volume up on the modem so I can here if some one is try to call but for purposes were I won't be close enough to the computer to here it I'd like to share my connection from my xp box to my ubuntu box.I enabled ics on xp box ,and on my ubuntu box I did this from the term:
sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0

sudo route add -net default gw 192.168.0.1

and my /etc/resolv.conf looks like this:

# resolv.conf created by pppconfig for provider
nameserver 204.73.103.12
nameserver 209.165.254.12

and thats all I did.Is there some thing else I need to do?when I type url in firefox it just searches for a while before giving up.

---

### Post by Hacim on 2006-10-16
bump

---

