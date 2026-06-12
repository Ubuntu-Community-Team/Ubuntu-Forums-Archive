---
title: "g++ compiler problems since upgrade..."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by l3vity on 2011-05-03
As part of my uni work I do a lot of C++ programming, which was one of the reasons why I tried Ubuntu in the first place (I have since grown to love it though).
Anyway, since upgrading to Natty everytime I boot up it seems that either the entire g++ compiler is missing or certain modules are and I get "unresolved includes inside <iostream>" etc. Each time I reboot some of these change, such as getting errors with ones I didn't before and others gaining errors.

Does anyone know a way to check it's still all working/up to date?

---

### Post by TeoBigusGeekus on 2011-05-03
You could try
```
sudo apt-get install --reinstall build-essential
```

---

