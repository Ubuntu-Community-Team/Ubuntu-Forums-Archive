---
title: "[SOLVED] help with update manager"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by tobeach on 2008-12-21
When I attempt to download updates.. get this message. How do I manually run??

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Cheers

---

### Post by Kareeser on 2008-12-21
Have you tried running that command stated, in the terminal?

dpkg --configure -a

---

### Post by drs305 on 2008-12-21
You must run the command with administrative powers (root):

```
sudo dpkg --configure -a
```

When is asks for your password, enter it even though you won't see any characters. Press enter when you are done.

Please mark the thread solved with the Thread Tools link at the top right of the first post if you have no other issues about this topic.

Welcome to ubuntu!

---

