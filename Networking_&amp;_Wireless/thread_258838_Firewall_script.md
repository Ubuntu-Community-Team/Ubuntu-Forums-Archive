---
title: "Firewall script"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by cyberjojo on 2006-09-16
Im setting up a firewall/router, but i cant find the place to put my firewall iptable script?

In the old days i used suse and there i was locaded in /etc/rc.d folder. 
In Ubuntu its no folder like that, they are called /etc/rc.0d rc.1d rc.2d etc....

can i make folder /etc/rc,d or is the script going somewhere else?


Thnx

Jojo

---

### Post by lcg on 2006-09-16
> **cyberjojo said:**
> Im setting up a firewall/router, but i cant find the place to put my firewall iptable script?

In the old days i used suse and there i was locaded in /etc/rc.d folder. 
In Ubuntu its no folder like that, they are called /etc/rc.0d rc.1d rc.2d etc....

can i make folder /etc/rc,d or is the script going somewhere else?
Ubuntu places the init scripts in /etc/init.d/. Symbolic links in one or more of the /etc/rcXd/ directories (X being a number between 0 and 6) then tell init in which runlevel and order to start or stop these scripts.

HTH,
Lars

---

### Post by neouser99 on 2006-09-17
Might i make a suggestion?

Check out shorewall. Its an awesome wrapper for the kernel firewall that makes managment super super easy, you won't regret it.

-neo

---

