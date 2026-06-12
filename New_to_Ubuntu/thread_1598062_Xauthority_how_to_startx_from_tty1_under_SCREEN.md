---
title: "Xauthority: how to startx from tty1 under SCREEN ?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-16
Hello

Under /dev/tty1 getty, there is a solution for startx under screen? 
I loged into getty tty1, then screen , 
then startx gives errors says that not possible.

Could it be passed over using .Xauthority?

---

### Post by Crusty Old Fart on 2010-11-02
This might work:
```

sudo service gdm start

```

---

