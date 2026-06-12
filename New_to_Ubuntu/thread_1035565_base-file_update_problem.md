---
title: "base-file update problem"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by AgTeq01 on 2009-01-09
Hi Everyone,
I have just installed and set up mythbuntu 8.10 (I am a first-timer with Linux). There is an alert on the screen near the network connection icon saying that there is an important security update available for base-files. When I try to get the update, I get this message: 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.ubuntu2.1_i386.deb) 404 Not Found IP: 91.189.88.40.80


Would appreciate suggestions on what is going on here & how to fix.

Thanks,

---

### Post by zvacet on 2009-01-10
In terminal type

```
cat /etc/apt/sources.list
```

and post output here.

---

