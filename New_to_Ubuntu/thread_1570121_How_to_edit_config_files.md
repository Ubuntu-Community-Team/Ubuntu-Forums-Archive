---
title: "How to edit config files?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by listerdl on 2010-09-07
Sorry i am being a bit dumb here but how do i edit a file in the /etc folder?

I need to edit a config file that is read only?

Do I do this via terminal and if so what are the commands! Thanks!!

---

### Post by munkyeetr on 2010-09-07
**CLI editor:**
```
sudo nano /etc/<filename>
```
CTRL-o to save changes, CTRL-x to exit

or

**GUI editor:**
```
gksudo gedit /etc/<filename>
```

---

### Post by listerdl on 2010-09-07
thanks buddy

---

