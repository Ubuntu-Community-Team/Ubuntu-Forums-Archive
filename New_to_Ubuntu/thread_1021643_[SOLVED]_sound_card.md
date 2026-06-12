---
title: "[SOLVED] sound card?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-25
Does anybody know a terminal command for checking what kind of sound card is installed? I've tried Google, and it's just not helping out this time.

---

### Post by coolbrook on 2008-12-25
Have you tried

lspci

---

### Post by abn91c on 2008-12-25
aplay -l

---

### Post by RomeReactor on 2008-12-25
Hi. You can also try:
```
sudo lshw -C multimedia
```

---

