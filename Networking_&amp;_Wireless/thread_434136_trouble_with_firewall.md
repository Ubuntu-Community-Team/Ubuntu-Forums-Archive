---
title: "trouble with firewall"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by MRiGnS on 2007-05-05
Firestarter recently started showing entries unkwon to me in its "acitve connections" window. (image attached)

I did not use bittorrent lately nor are the ports at the moment opened/forwarded. not by my router and not by my desktops iptables. So i dont know where this connections do come from. I ran clamav (found nothing) searched the output of ps aux but found nothing causing this. im kind of clueless


It also blocks some services called back orifice 2k. ya, I know it's this trojan/networkadmin tool.

---

### Post by Floppyjoe on 2007-05-05
Do you have other people that have access to the computer that might download stuff that you might be unaware of?A Child perhaps or someone else?

---

### Post by MRiGnS on 2007-05-05
No, I'm the only one using this pc.

now i additionally blocked the IPs of the services via terminal but firestarter is still showing them as active and not as blocked connections.

neither netstat -pn -l -A inet && netstat tunap nor netstat -pn -l -A inet are showing something suspicious, well they aren't showing these "spooky" connections at all.

users and roots running tasks seem to be innocent.

---

