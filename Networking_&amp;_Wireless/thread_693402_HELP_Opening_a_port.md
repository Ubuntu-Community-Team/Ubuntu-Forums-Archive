---
title: "HELP: Opening a port"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by cjtjamandra on 2008-02-11
I want to open the port 1983 using this command:

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 1983 -j ACCEPT

but it seems not to be working because the port is still closed. i have issued the command:


netstat -an | grep "LISTEN "


and still, the port 1983 is not there... please help me.. i have tried so many iptables command in opening a port but nothing have worked... thx in advance...

---

