---
title: "Unable to start iptables-persistent service?"
date: 2016-12-06
forum: Networking &amp; Wireless
---

### Post by eezacque on 2016-12-06
Just discovered that iptables-persistent is no longer doing its job (running Ubuntu 16.04)
The package is installed, but the service is not starting:

$ sudo service iptables-persistent start
Failed to start iptables-persistent.service: Unit iptables-persistent.service not found.

There is no file iptables-persistent in /etc/init.d

Any clue?

---

### Post by eezacque on 2016-12-06
[SIZE=2][FONT=arial]Looks like iptables-persistent was replaced by netfilter-persistent[/FONT][/SIZE][SIZE=3]

Edit: netfilter-persistent does not save/restore my iptables to survive a reboot!

So, is there a standard way to make iptables rules persistent in Ubuntu 16.04
 [/SIZE]

---

