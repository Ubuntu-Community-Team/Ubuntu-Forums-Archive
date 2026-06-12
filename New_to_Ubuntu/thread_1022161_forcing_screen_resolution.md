---
title: "forcing screen resolution"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ditobarata on 2008-12-26
hi,

does anybody ever try to force the ubuntu screen resolution?

i installed ubuntu intrepid in my acer 4520. it's normal screen resolution is 1280x800 and i wish to force it to 1760x1100. Does anybody can tell me how to do it?

---

### Post by stoogiebuncho on 2008-12-29
You could try messing with your /etc/X11/xorg.conf file (back it up first), but people have really mixed results with that.  What works for one person doesn't seem to work for the next.  It depends a lot on your graphics card.

To make a backup:
```

cd /etc/X11
sudo cp xorg.conf xorg.conf.backup

```

To edit:
```
sudo gedit xorg.conf
```

I recommend finding a day when you'll have some time, and use Google to see how other people have done it.  Good luck.

---

