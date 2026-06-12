---
title: "ping arp -a"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2006-12-27
Hi all,

I am in the office right now and trying to figure out how to find out a mac address of another machine that is in the office. Usually with Windows I was used to use the:

ping arp -a

command to resolve the mac address, is there a similar command that I can run in shell to find out about mac address of other machines in the same network?

would be very thankful for your help.

aliyanage

---

### Post by aliyanage on 2006-12-27
sorry guys, just saw that it usually shows the MAC address as soon as I do a scan with nmap, but the issue was that I wasn't in the same subnet as the other machines.

---

### Post by terrrorr on 2006-12-27
Well


Try this one

arping <ip-address>

---

### Post by aliyanage on 2006-12-27
thanks man, that's also a lot easier than scanning the range :-D

---

