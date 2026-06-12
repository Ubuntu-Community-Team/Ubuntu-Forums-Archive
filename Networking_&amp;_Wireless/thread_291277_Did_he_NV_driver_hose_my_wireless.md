---
title: "Did he NV driver hose my wireless?"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by pastorjay on 2006-11-02
Hey all, 

I just installed the Nvidia driver with Automatix2.  I shut the laptop down, and went to Panera.  Wireless has been working flawlessly, even up to the point of installing the NV driver.  Now, I am sitting at panera, and my wireless will not function.  I did a search and did not find anything, so, the question is:

Did my wireless get messed up by installing the NV driver?  If so, how can I fix it?

Thanks!
Jason

Dell e1705
NV 7900GS
60GB HDD
2GB Ram
Dell wireless (Broadcom 4311)

---

### Post by Paerez on 2006-11-02
this may be a problem with the "linux-restricted-modules`version`" package. It contains nvidia drivers, ati drivers, and some network drivers. I would try installing it or uninstalling it (basically mess with it) and see if that helps.

Also, what kind of wireless?

---

### Post by pastorjay on 2006-11-02
oops!  SHould have listed it as well. It is a broadcom 4311 (Dell).  It was a pain getting it working, so needless to say I was a little ticked when it stopped working!

---

### Post by Paerez on 2006-11-02
I would guess its the restricted drivers, then.

I would suggest re-doing the broadcom install. The automatix-nvidia may have overwritten some of your broadcom stuff.

---

