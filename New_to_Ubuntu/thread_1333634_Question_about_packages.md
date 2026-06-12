---
title: "Question about packages"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by miguel_d on 2009-11-21
I wanted to know if when i select a package and mark it for removing completely, everything that the synaptic downloaded and installed is removed or there are some things that stay in the computer?

Thanks:)

---

### Post by Norm24 on 2009-11-21
Some "stuff" does get left behind.Sometimes a reboot takes care of it.

Also try running this in terminal after removing something:
```
sudo apt-get auto clean

sudo apt-get autoremove
```

---

### Post by miguel_d on 2009-11-21
thanks, the second command worked

---

