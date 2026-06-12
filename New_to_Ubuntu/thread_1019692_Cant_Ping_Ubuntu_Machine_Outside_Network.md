---
title: "Cant Ping Ubuntu Machine Outside Network"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-23
Hello,

I recently posted an issue in ssh from outside my network, but I dont believe the issue is ssh. I am able to ping and ssh into my ubuntu machine from a labtop, but i receive a time-out when i try and ping the machine from outside the network.

I have disabled the ubuntu firewall and have d-link router turned on, with port-forward for 22 and 80.

Funny thing is I can connect to this address externally with my laptop by typing the ip address in Internet Explorer since I have apache running, but I cant ping to it ?

Any ideas ?


Thanks
Frank

---

### Post by ken22 on 2008-12-23
What IP are you pinging. It won't work if you ping the local address assigned to your machine on your own network.

---

### Post by Titan8990 on 2008-12-23
Have you forwarded the ports on the router?

Have you configured your router to accept anonymous requests? Have you configured your router to accept ICMP (ping) packets?

---

### Post by Kareeser on 2008-12-23
Assuming you're not pinging a private IP (192.168.*.*)...

> Have you configured your router to accept ICMP (ping) packets?
That.

---

