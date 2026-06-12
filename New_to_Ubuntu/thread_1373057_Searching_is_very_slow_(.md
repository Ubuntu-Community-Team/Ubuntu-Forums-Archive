---
title: "Searching is very slow :("
date: 2010-01-05
forum: New to Ubuntu
---

### Post by putu.sundika on 2010-01-05
Dear all, why searching is very slow on UBUNTU 9.04 (nautilus) ? I run UBUNTU on Netbook Axioo Atom Memory 2G. If compare with M$WIN, UBUNTU show the result only when totaly finish searhing. Can I change that ? just like M$WIN does ?

---

### Post by Zoot7 on 2010-01-05
What are you using to search?

**locate** over the command line is very quick. The only snag is you've to run **sudo updatedb** to update the database periodically. 
Use it like this:
```
locate <what you're looking for>
```

A good frontend or GUI to locate is catfish.
```
sudo apt-get install catfish
```

---

### Post by putu.sundika on 2010-01-06
locate is very fast on terminal.
I try to use search box on Nautilus. Result comes very slow and result is no good. 
Any idea ?

---

### Post by Zoot7 on 2010-01-06
Searching with nautilus is pretty slow yeah, but I don't know if it's any slower than say the search in Windows.
I suggest you give catfish a shot. :)

---

### Post by putu.sundika on 2010-01-06
> **Zoot7 said:**
> Searching with nautilus is pretty slow yeah, but I don't know if it's any slower than say the search in Windows.
I suggest you give catfish a shot. :)

i'll try catfish. thnks.

---

