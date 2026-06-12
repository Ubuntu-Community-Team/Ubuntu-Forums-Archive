---
title: "How do I get permission to copy files and edit folders on an external drive?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by hortstu on 2010-06-02
It is basically empty and formatted to one large partition of ext 3 within an extended partition.

I'm using the 10.04 boot disc on a borrowed computer that only runs windows.

Thanks for any help.

---

### Post by nhasian on 2010-06-02
you should automatically have write access to an external usb hard disk when it auto mounts.  for some reason if you don't have access you can launch nautilus with super user privilege by pressing F2 and entering:

```
gksu nautilus
```

be careful what you move or delete from your drive, since you will have total access you dont want to bork your system.

---

### Post by hortstu on 2010-06-02
thanks

---

