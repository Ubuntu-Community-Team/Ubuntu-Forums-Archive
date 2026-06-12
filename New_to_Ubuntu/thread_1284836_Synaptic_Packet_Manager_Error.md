---
title: "Synaptic Packet Manager Error"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by anuj@iit on 2009-10-07
While i am opening Synaptic packet manager, this error is being displayed..

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I have run that specified command but still it is showing the same error.
Also, i couldn't figure out what the second error is all about.
Please help me out..Thanks.

---

### Post by Peter09 on 2009-10-07
did you run the full command - using sudo

```
sudo dpkg --configure -a
```

---

### Post by 3rdalbum on 2009-10-07
> **anuj@iit said:**
> While i am opening Synaptic packet manager, this error is being displayed..

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I have run that specified command but still it is showing the same error.
Also, i couldn't figure out what the second error is all about.
Please help me out..Thanks.

You're running an old version of Ubuntu? Unless the release notes tell you not to, you should be running the latest Ubuntu. The next version, 9.10, comes out at the end of the month.

The current Ubuntu version, 9.04, specifies the correct command in that error message, which is "sudo dpkg --configure -a".

---

### Post by anuj@iit on 2009-10-07
Yes i got it, thanks a lot to everyone!!

---

