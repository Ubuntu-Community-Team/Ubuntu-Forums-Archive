---
title: "I can't delate items in my waste basket"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by jorge ortega on 2009-01-16
My waste basket doesn't let me delate certain items. Could I use the terminal for that and if so how?
Thanks

---

### Post by sisco311 on 2009-01-16
```
sudo chown -R $USER: ~/.local/share/Trash/
```then try again.

---

### Post by jorge ortega on 2009-01-16
Sisco,
I did as you said but I still can't delate them. More ideas?

---

### Post by sisco311 on 2009-01-16
open the file manager as root:
```
gksu nautilus ~/.local/share/Trash/files
```

---

### Post by jorge ortega on 2009-01-16
Thanks for that; for some reason the folder got duplicated in the waste basket. After doing as you said one of the items is gone but the other still there, I can't still delate it.

---

