---
title: "Need help can't log into Ubuntu"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-31
Well I partition the hard drive so I could install Windows and I did, but I don't know why but I couldn't install my internet :s or my damn monitor so the resolution was mest up. And well two hours of trying to fix the internet I got mad and deleted the partion and gave it back to Ubuntu but now I can't load onto Ubuntu.

Right now I'm using the Use Ubuntu without any changes to computer option on the LiveCD...

How do I get GRUB back?

Edit:nvm I think I got it with these [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

sorry but ill repost if that worked

---

### Post by jelle_ on 2009-03-31
installing windows xp overwrote grub. this means you cannot boot ubuntu. to fix this, open a terminal in the LiveCD and type

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by lil_kid1333 on 2009-03-31
yeah I fixed it thanks dude!

But I want to know why my damn Windows didn't detect my internet! I even installed the cd that came when I got internet and nothing... God it sucks man...

---

