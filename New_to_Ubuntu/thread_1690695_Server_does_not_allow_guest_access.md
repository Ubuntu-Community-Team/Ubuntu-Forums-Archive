---
title: "Server does not allow guest access"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by mistergoomba on 2011-02-18
I set guest access on a folder (an external hard drive to be exact), but when I try to access it from my Mac, I am told that the server does not allow Guest access.

---

### Post by Cracklepop on 2011-02-18
If you want the server to use an external disk you can't let Ubuntu mount the disk automatically, you need to put an entry into fstab for it.

---

### Post by mistergoomba on 2011-02-20
Great, thanks for the reply! I got this to work by entering "force user = <username>" into my samba config file :}

---

