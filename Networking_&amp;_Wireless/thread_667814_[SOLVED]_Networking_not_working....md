---
title: "[SOLVED] Networking not working..."
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by zhimsel on 2008-01-14
Hey forums,

I just had a problem with X and successfully fixed it. When I got it back up and running, I find that my networking is not working. I've tried manually assigning IPs and using DHCP (using the Gnome Network Manager and manually editing /etc/network/interfaces" and "Roaming Mode".

I'm getting a link light, and my Xbox 360 can connect with the same cable, so it's not physical. For some reason, it just does not want to communicate. 

I will supply any config, /proc, etc files needed.

Please help! ='[

---

### Post by wieman01 on 2008-01-15
First of all please post:
> sudo cat /etc/network/interfaces
> route
> sudo /etc/init.d/networking restart
> sudo lshw -C network

---

### Post by zhimsel on 2008-01-15
I'm actually not sure why, but it seems to be working again. Randomly after a restart...

Hmmmm... =]

---

