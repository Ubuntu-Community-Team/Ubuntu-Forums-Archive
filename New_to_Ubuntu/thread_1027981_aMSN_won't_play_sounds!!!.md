---
title: "aMSN won't play sounds!!!"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by mangcool on 2009-01-01
I have aMSN 0.97.1 installed on my Ubuntu 8.04 (Heron). It makes me angry because it won't play any sound if there's someone logging in, logged out, etc.

How can I fix it?

---

### Post by stderr on 2009-01-01
Not sure about aMSN; I last used it many years ago before I found out about Pidgin. I would advise using Pidgin instead, since it's installed by default and works excellently with a whole host of different protocols (MSN/ICQ/AIM/YIM/IRC/Google Talk/you name it). Also integrates with the status/logoff/shutdown etc button. 

If you want to keep using aMSN for some reason, then I'm sure someone else will oblige with a solution momentarily :)

---

### Post by fermin on 2009-01-18
I had this problem with some version of aMSN before. Check that the aplay command is set in preferences -- other -- sound server; mine looks like

```
aplay $sound
```

---

