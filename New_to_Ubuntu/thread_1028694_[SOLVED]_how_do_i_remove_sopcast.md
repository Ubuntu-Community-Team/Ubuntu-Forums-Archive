---
title: "[SOLVED] how do i remove sopcast?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-02
anyone know how i can remove sopcast from ubuntu i got it from a deb file online and i can't find the package in synaptic to remove it

---

### Post by Michael.Godawski on 2009-01-02
hi, 

If you know the exact name of the package you can try in terminal:

```
sudo dpkg -r package_name
```

---

### Post by mamamia88 on 2009-01-02
that would work if i actually new the name of the package is there a way of finding it out?

---

### Post by adult swim on 2009-01-02
do you remember where you downloaded it from?

---

### Post by mamamia88 on 2009-01-02
ok i found it thanks for the advice i was just spelling it wrong by one letter the entire time

---

### Post by kwacka on 2009-01-02
deleted

---

### Post by crjackson on 2009-01-02
Try this:

```
sudo dpkg -r gtk-sopcast
```

---

### Post by crjackson on 2009-01-02
Never mind, you marked it solved by the time I posted :|

---

