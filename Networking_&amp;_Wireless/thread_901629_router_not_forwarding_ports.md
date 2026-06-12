---
title: "router not forwarding ports"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by elchico04 on 2008-08-26
I am trying to setup a SSH server and I have no idea why I can't forward any ports!

My server has a static IP.
I made sure that there is no firewall running
I went to my router's gui and forwarded port 22 to the aforementioned static IP.
If I try to connect from another computer I get "connection refused"
I did a port scan and port 22 is not responding.

I tried forwarding port 80 and scanning it. I got the same result.

What do I need to do to get my ports to forward correctly?

---

### Post by jigsaws on 2008-08-26
Looks like problem with your router and IP forwarding, not with Ubuntu.
Check if you forward port 22/tcp to port 22 of your server. Restart router.
Then make sure that you are trying to connect to YOUR router from outside.

Check if you can ssh to your server from internal network. Check netstat -lt . Does your sshd lissten on eth0 or *?

---

### Post by elchico04 on 2008-08-26
...a router restart seemed to do the trick.

thanks for pointing it out to me.

---

### Post by elchico04 on 2008-08-26
...a router restart seemed to do the trick.

thanks for pointing it out to me.

---

