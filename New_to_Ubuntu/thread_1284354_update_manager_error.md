---
title: "update manager error"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-10-06
i tried updating today and got this
```
E: Can't write /root/.synaptic/selections.proceed
```
i haven't changed anything since the last update that i know of. what's the problem?

---

### Post by tomBorgia on 2009-10-08
Are you running the update with root (or sudo) privs?

If so then check the permissions on your /root/.synaptic folder.. they should look like this -


```
drwx------  3 root root 4096 2009-09-21 09:20 .synaptic

```
```
-rw-r--r--  1 root root   40 2009-10-07 08:47 selections.proceed

```

---

