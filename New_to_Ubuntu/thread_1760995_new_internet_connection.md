---
title: "new internet connection"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by scorpious on 2011-05-17
I've got a new internet connection (pppoe) and don't know how to connect to it through ubuntu.

In windows I'd go
set up connection>>connect to internet>>PPPoE>>Username@prepay.snap.net.nz, password and connection name>>connect

How would I go about doing this with ubuntu?

cheers

---

### Post by mick222 on 2011-05-17
It should just find it if not go to the network icon on the top panel click and select edit connections. You don't say whether it s wireless or not.

---

### Post by scorpious on 2011-05-17
wired

---

### Post by gandaran on 2011-05-17
> **scorpious said:**
> I've got a new internet connection (pppoe) and don't know how to connect to it through ubuntu.

In windows I'd go
set up connection>>connect to internet>>PPPoE>>Username@prepay.snap.net.nz, password and connection name>>connect

How would I go about doing this with ubuntu?

cheers
from the network manager panel icon » edit connections, use the DSL tab for pppoe setups or from CLI type in terminal
```
sudo pppoeconf
```

---

### Post by scorpious on 2011-05-17
used```
 sudo pppoeconf
```that was very easy. 
Isn't Ubuntu fantastic?

thanks guys

---

