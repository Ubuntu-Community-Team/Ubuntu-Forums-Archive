---
title: "Use specific wlan per user"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by bewareofthephog on 2014-04-16
I have two users setup on my box.  I'd like User1 to only use eth0 and User2 to only use wlan0, is there a way to do this on Ubuntu?

---

### Post by Ferry_Kristianto on 2014-04-16
It think its impossible to hide / disable an interface from user login.
How about a cron job to check the current user?
You can add in cron a firewall script to reject traffic from certain interface. That will prevent a username to connect through certain interface.

---

