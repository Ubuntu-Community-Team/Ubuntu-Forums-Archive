---
title: "Resolving Broken - Ideas?"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by thejerz on 2006-12-23
Friends,

I installed bind9 to limited success a few weeks ago.  The second bind9 started working, resolving domains stopped working.  Right now, I cannot ping, nslookup, etc. any domain from my Ubuntu Server.  The server is in a colocation facility so I have to be careful not to break anything that requires an in-person trip!

I decided to uninstall bind9 so I could update the server and find the problem.  Although apt-get install returns dozens of "cannot resolve" messages, "apt-get remove bind9" seems to have worked.  Now that bind9 is gone, I still cannot resolve any domains.

My /etc/resolv.conf file:

nameserver 127.0.0.1
nameserver 65.57.104.50
nameserver 65.57.104.51

Those are the two IPs provided by the colocation facility.

Any idea on why I can't access anything???  Please help!  

Thanks,
thejerz

---

### Post by djRobbieF on 2006-12-23
I presume you have SSH working on the server so you can remote-admin it without having to go to the collocation site?

---

### Post by thejerz on 2006-12-23
Yes; that is correct.  Right now I'm doing:

ssh me@65.57.104.50

to log in.

Thanks!

-thejerz

---

### Post by djRobbieF on 2006-12-23
Check your private messages.

---

### Post by djRobbieF on 2006-12-23
Guess you've disappeared  ;)  I'm gonna jet for tonight.  Have a great Christmas.

---

