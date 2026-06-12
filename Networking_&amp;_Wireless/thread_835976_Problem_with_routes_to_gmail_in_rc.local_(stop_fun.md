---
title: "Problem with routes to gmail in rc.local (stop functioning)"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by RoyOrbison on 2008-06-21
Dear friends, this is my problem:

I use gmail as pop3 and imap servers. My network consist of 40 ubuntu`s terminals  ,without default gateway. They use a proxy to search internet (IPCOP).
I need to create a route to gmail servers (pop.gmail.com 74.125.47.109 and 111) and imap.gmail.com 66.249.83.109)

I wrote this in /etc/rc.local

route add -host pop.gmail.com gw 10.0.100.1  (neither netmask or device)
route add -host imap.gmail.com gw 10.0.100.1 (neither netmask or device)

It worked, but later (one or two hours later) it stopped working.
I can´t ping pop.gmail.com or imap.gmail.com, but the route (route -n) still exist.


I had to change default gateway (to another router) to reactivate the route again. It happened again the following day, then I have to write the initial gateway again, to be able to work.

What  is happening?

Is  there another way to deny full internet acces to these people (no default gateway) , and make route to gmail?

Is DNS order important in this case? I dont have DNS server in LAN. I have resolv.conf with an router IP as nameservers.

NOTE: If I put a default gateway in /etc/network/interfaces, all work perfectly.

Sincerely thanks

---

