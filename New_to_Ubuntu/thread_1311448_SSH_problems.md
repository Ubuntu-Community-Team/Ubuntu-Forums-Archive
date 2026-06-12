---
title: "SSH problems"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dougie_boy on 2009-11-02
Ive got a putty client on windows and can only log on to my websever locally. If i try to login over the net (my hostname or my IP) i get the following message

> network error connection refused

my firewalls (router and UFW) have port 22 allowed and i am at a loss to why this would be the case. any ideas?

---

### Post by teward on 2009-11-02
mhm.  Are you connected to a router?  If yes, you need to forward your ports on the router, because the router auto-denies the connection until you tell it not to.

---

### Post by teward on 2009-11-02
Second post:  This WILL be the case also with using SSH on Linux/Ubuntu

---

### Post by ZankerH on 2009-11-02
Sounds like you need to open up port 22 on your router.

---

### Post by dougie_boy on 2009-11-02
22 port is forwarded to the ip of the server on the router, the same on UFW. i cannot think why i would get this error then.

---

### Post by dougie_boy on 2009-11-02
ghost in the machine, works fine now. can only think the router needed to update.

---

### Post by ZankerH on 2009-11-02
> **dougie_boy said:**
> 22 port is forwarded to the ip of the server on the router, the same on UFW. i cannot think why i would get this error then.

Run

```
ifconfig eth0
```

On the server. That should give you the local IP (it's listed under inet addr). You may need to replace eth0 with the network interface you're using.

edit: Glad to see you got it worked out.

---

