---
title: "restricted codecs installation problem"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by anthonyleamy on 2009-03-10
While installing the package of restricted codecs from mediubuntu my pc froze during installation of the java stuff. I aborted the process and tried to repeat the from the beginning.
Got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do I approach this? Tried adding the sudo command before it, but not at all sure about the semantics of the these commands.

All help would be appreciated

---

### Post by taurus on 2009-03-10
Yes, just run that command with root privilege.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get **upgrade**
```

---

### Post by anthonyleamy on 2009-03-10
Managed to deal with that thank you. However, when faced with missing dependencies was faced again  with frozen screen asking me to accept java licensing agreement etc. Clicked on ok but no movement at all. Seems to freeze.
Will try again tomorrow.
Thanks a lot

---

### Post by oldos2er on 2009-03-10
> **anthonyleamy said:**
> Managed to deal with that thank you. However, when faced with missing dependencies was faced again  with frozen screen asking me to accept java licensing agreement etc. Clicked on ok but no movement at all. Seems to freeze.
Will try again tomorrow.
Thanks a lot

 Hit Tab to highlight 'ok,' then Enter.

---

