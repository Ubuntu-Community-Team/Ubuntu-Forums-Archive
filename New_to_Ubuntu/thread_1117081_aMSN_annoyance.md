---
title: "aMSN annoyance"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by magnavar on 2009-04-05
So, I'm trying to install aMSN, and I'm doing everything right. Except when I try to configure it, it always pulls up the error that it can't find /usr/lib/tkConfig.sh. I checked it out, and I found that that is because it's in an additional folder. How would I move this, since I don't know how to get into root to do so?

---

### Post by ibuclaw on 2009-04-05
Did you get the build-deps for amsn?
```
sudo apt-get build-dep amsn
```


Regards
Iain

---

