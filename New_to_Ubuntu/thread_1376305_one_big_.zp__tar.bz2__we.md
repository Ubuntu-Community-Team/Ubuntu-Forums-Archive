---
title: "one big .zp / tar.bz2 / w/e"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by FreezWay on 2010-01-09
how cam i compress a huge folder (over 14GB) of varying content into a compressed format... More importantly I need to do this from a live CD, this is for rescuing files from comps with windows error and not taking up massive amounts of space.

---

### Post by markjensen on 2010-01-09
Can you not right-click and select something like "Create Archive..."?

I am running Xubuntu and using Thunar as my file manager, but if you are running Gnome I would think that you would have this option, too.

---

### Post by FreezWay on 2010-01-09
theres "compress" but it spits errors if i do something too big.

---

### Post by sandyd on 2010-01-09
> **FreezWay said:**
> theres "compress" but it spits errors if i do something too big.
```

tar -z -c ***foldername*** ***archivename***.tar 

```

---

### Post by J V on 2010-01-09
hmm...

```
sudo tar -Mcaf "saved.tar.gz" -C "<directory to compress from>" --recursion *
```

---

