---
title: "Package manager"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by timoftheecat on 2009-03-31
Please help me with this...
error message when trying to do updates...red dot with dash in the middle

E: Type 'taller' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by adult swim on 2009-03-31
go to a terminal, applications>accessories>terminal, and enter in ```
cat /etc/apt/sources.list
``` then paste the results here

---

### Post by llamabr on 2009-03-31
you can also go right to the line with nano using

```
nano +47 /etc/apt/sources.list
```

may help you trouble shoot.

---

### Post by 3rdalbum on 2009-03-31
Remove any lines that don't start with "deb" or the hash symbol ("#") from your sources list.

---

### Post by timoftheecat on 2009-03-31
That did it! Thank you thank you thank you!!! I love this! Thank you to everyone who responded to my need for help....I very much appreciate you.

---

### Post by hyper_ch on 2009-04-01
if you have troubles again, you can use my repo generator to re-create your sources.list. Have a look at my sig.

---

