---
title: "disconnecting from server"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-02-27
Whenever i try sudo aptitude get...
my terminal tries to connect to the server of my college. I removed the IP address of that server from proxy settings but it still tries to connect. How do I avoid it?

---

### Post by fabricator4 on 2011-02-27
> **RobikShrestha said:**
> Whenever i try sudo aptitude get...
my terminal tries to connect to the server of my college. I removed the IP address of that server from proxy settings but it still tries to connect. How do I avoid it?

A possible reason is that there's a firewall that is blocking the port that Ubuntu uses for updates, checking repositories etc.

The solution is normally to change this to port 80 which is unlikely to be blocked.  Try Googling for this solution and you should find a few methods.


Chris.

---

