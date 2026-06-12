---
title: "Can't install build essential"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-02-16
Hy folks!

I have a problem: I cannot install build-essential. If I try to install it I get:
```
build-essential:
  Depends: g++ (>=4:4.3.1) but 4:4.2.3-1ubuntu6 is to be installed
```

I think it is a problem concerning dependencies I think, but i don't know how to fix it.
Any help would be appreciated.

---

### Post by nothingspecial on 2010-02-16
Try ```
sudo apt-get install -f
```

Then try again.

---

