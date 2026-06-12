---
title: "PC doesn't recognize proprietary drivers"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by paker on 2010-07-26
BACKGROUND:
10.04 had a few issues critical to me. I downgraded to 9.10 - fresh install from CD after reformating the root directory. 

PROBLEM:
1) I don't get the usual prompt for proprietary hardware drivers, specifially, nvidia driver v. 185 and B43 wireless driver. 
2) No update prompt.

I force-checked proprietary hardware drivers. Nothing was found. 
Again, open Update Manager. No updates are listed.

Something not right?

---

### Post by wojox on 2010-07-26
Copy and paste in your terminal

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by Res2216firestar on 2010-07-26
What graphics card do you have? And you might check the update manager settings for the update prompt.

---

### Post by paker on 2010-07-26
Thanks. I use nvidia.

---

### Post by sandyd on 2010-07-26
connect computer to internet thru ethernet cable, then tri again.

---

