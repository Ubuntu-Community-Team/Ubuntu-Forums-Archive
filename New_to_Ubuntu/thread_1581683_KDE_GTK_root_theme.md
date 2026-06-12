---
title: "KDE GTK root theme"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by sandyd on 2010-09-25
Can someone give me a pointer on how to make GTK applications run as root look the same as GTK applications not run as root?

---

### Post by qamelian on 2010-09-25
In /root, create a symlink to the .themes folder in your home folder. 

```
cd /root
sudo ln /home/user_name/.themes
```

---

