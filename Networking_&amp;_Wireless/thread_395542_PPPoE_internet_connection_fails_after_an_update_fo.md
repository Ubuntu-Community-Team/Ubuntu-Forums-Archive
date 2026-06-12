---
title: "PPPoE internet connection fails after an update for Feisty Fawn Beta"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by ThijsN on 2007-03-28
I installed Ubuntu Feisty Fawn Beta from the LiveCD.

When running of the LiveCD, and directly after the installation, the PPPoE connection is perfect and a breeze to set up (using 'pppoeconf').

Right after the installation, Ubuntu mentioned a lot of new updates and asked if I wanted to install them. I did and after a reboot (I guess because of a kernel update - can't remember exactly) the PPPoE connection failed. I can post the output of 'plog' if it helps (I am on Windows XP right now).

I installed Feisty Fawn twice from the LiveCD and encountered this connection problem twice. 

Does anyone have a clue if this is the updates fault or something else and if it will be fixed before the official April release of Feisty? Is there anyone who has the same trouble?

Many thanks.
Thijs


PS. I posted a bug report on Launchpad describing this problem: [#97451]("https://launchpad.net/bugs/97451")

---

### Post by infoseeker on 2007-03-30
I installed Ubuntu Feisty Beta yesterday and I am having the same problem.  The connection seems to come up normally on bootup and ppp0 is listed under 'ifconfig', but NO internet.
The only way to solve this for me is to terminate ppp0 by doing
```
sudo poff
```
and then```
sudo pon dsl-provider
```

---

