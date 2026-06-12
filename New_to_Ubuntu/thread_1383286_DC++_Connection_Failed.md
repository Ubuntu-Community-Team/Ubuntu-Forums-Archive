---
title: "DC++ Connection Failed"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by CJWW1989 on 2010-01-17
I recently downloaded the DC++ client that Ubuntu 9.10 uses and every time I try and connect to a room it fails. I have MoBlock running FYI. Can anyone help me?

---

### Post by ikt on 2010-01-17
All the correct ports forwarded?

---

### Post by jre on 2010-01-17
No idea what DC++ is, but you can check live if MoBlock blocks anything by typing
```
tail -f /var/log/moblock.log
```

So when you test DC++ and see a block in the logfile at the same time, then you have to add some whitelisting rules to MoBlock. See here [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) or ask, when you need help.

---

