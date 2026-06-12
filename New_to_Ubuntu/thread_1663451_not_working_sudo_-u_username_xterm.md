---
title: "not working: sudo -u username xterm ?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by honeybear on 2011-01-09
Hello,

I try to run this command but it is not allowed by hte system. the user exists, but it seems it hangs at the password.

What's the problem please?

---

### Post by TeoBigusGeekus on 2011-01-09
It's working for me (arch, xterm 267-1).
Does
```
su username && xterm
```
suit your task?

---

### Post by honeybear on 2011-01-09
> **TeoBigusGeekus said:**
> It's working for me (arch, xterm 267-1).
Does
```
su username && xterm
```
suit your task?

I tried:

```
sudo -l username xterm 
```

and it is not working... 


Thank you in advance,

---

