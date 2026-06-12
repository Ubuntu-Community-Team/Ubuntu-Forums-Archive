---
title: "quick terminal question"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-10-31
trying to move some files into a section that i dont have permisison to access (dictionary files into stardict) - what commands do i need to type in the terminal to move them where they need to go?

thanks

---

### Post by NoaHall on 2009-10-31
To copy:
```
sudo cp /home/user/filename /location/
```
or to move:
```
sudo mv /home/user/filename /location/
```

---

### Post by gwilkins82 on 2009-10-31
false alarm, figured it out.  (sudo mv)

---

### Post by emigrant on 2009-10-31
or if you want to do it in gui:
```

sudo nautilus

```

and in the nautilus window you can move/copy freely. but be cautious not to DELETE files which would harm the system.

---

### Post by Bölvaður on 2009-10-31
> **emigrant said:**
> or if you want to do it in gui:
```

sudo nautilus

```and in the nautilus window you can move/copy freely. but be cautious not to DELETE files which would harm the system.


very close it is gksudo or gksu



so alt+F2
```
gksu nautilus
```

---

