---
title: "system only boots to terminal after install"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by floatingpoint on 2010-10-17
so it just boots to terminal, no gui, no installation complete message. so i tried to sudo apt-get ubuntu-desktop, this package doesn't exist, what is the correct package? or an alternative solution?

---

### Post by Sealbhach on 2010-10-17
It should be 

```
sudo apt-get install ubuntu-desktop
```

It's possible that you installed the server edition by mistake, which comes without a desktop.

.

---

### Post by Fungus on 2012-08-23
I have a laptop with core2 duo and intel 965 video using Lucid 10.04 LTS.  I had completely lost my Xwindow graphic interface.  

This solution worked for me!

---

