---
title: "Stuck in low graphics mode"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by abeautifulplace on 2009-03-23
After installing and uninstalling 'Envy', I am stuck in low graphics mode and an 800x600 square in the middle of my screen. I've tried nearly everything I can think of, but still no luck.
Any suggestions on how to fix this?

---

### Post by ptn107 on 2009-03-23
You may try reconfiguring the X server from scratch with this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

