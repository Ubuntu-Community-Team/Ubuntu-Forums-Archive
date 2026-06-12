---
title: "Server not listen on port"
date: 2015-06-30
forum: Networking &amp; Wireless
---

### Post by webservfer on 2015-06-30
Trying to set up a don't starve together game server. The sever says its listen on port 10999 and gives no errors, but netstat  shows no open ports. Iptables is allowing all traffic through. Does anyone have any idea what's going wrong? I really feel like its the OS blocking the traffic.

---

### Post by Lars Noodén on 2015-06-30
How are you starting the server and are you checking [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html) using -l option?

```

netstat -ntulp
netstat -ntulp | grep 10999

```

---

### Post by webservfer on 2015-07-02
Looks like I was using the wrong netstat options. Yeah I ran the server then netstat -tan or just netstat, which doesn't show everything. 
Thanks so much. now I need to learn more netstat commands.

---

