---
title: "Wine Setup Error Message"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-29
Hey there, I received this error message when I tried to install wine?  What is going on? (pic attached)

---

### Post by webofunni on 2011-05-29
is this 

```

/usr/lib/wine

```

works ?

---

### Post by TAspr on 2011-05-29
> **webofunni said:**
> is this 

```

/usr/lib/wine

```works ?

No, it does not, and when I run the command that you gave me, it does nothing as in the picture.

---

### Post by webofunni on 2011-05-29
can you execute this 

```

dpkg -S /usr/lib/wine
dpkg -l | grep -i wine

```

---

