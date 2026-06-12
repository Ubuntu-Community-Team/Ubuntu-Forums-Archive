---
title: "how I can really empty ubuntu trash ?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-10
I am trying to empty the trash but I can not.
I tried all commands which are mentioned in [http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html) with no luck.

when I open the trash in gnome, it has some content which I can not delete. when I try to change the permission of the content it does not allow me....


Is there any way to use root permission and empty the trash?
I tried and opened a nautilus using root (gksudo) and then I tried to open trash:/// with no luck.


thanks

---

### Post by bodhi.zazen on 2009-02-10
Did you try ;

```
**sudo rm -rf ~/.local/share/Trash/files/*
```**

---

### Post by legolas_w on 2009-02-10
You are the man, this command worked charming.

Thanks.

---

### Post by Old Old Duffers on 2009-02-10
Same problem with emptying trash.  It worked
for me also.  He is the Man!

---

