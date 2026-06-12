---
title: "Somewhat lame enlightenment question."
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2009-03-12
I love the enlightenment desktop, but I can't seem to connect to any wireless networks in it. Everything works fine in GNOME, but I can't get it to work in Enlightenment. Odds are the answer is something simple, but I can't figure it out. Any ideas?

---

### Post by kanikilu on 2009-03-12
I don't use enlightenment, but I'm guessing you'd need some sort of wireless connection manager :?:

Have you tried WICD?

---

### Post by kellemes on 2009-03-12
You need to start "nm-applet"


You can put it in your ~/.xinitrc if you wish..
```
#!/bin/sh
nm-applet &
exec enlightenment_start
```

---

