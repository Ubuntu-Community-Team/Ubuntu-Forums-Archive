---
title: "cli code to exact same as double click file."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by 569874123 on 2009-02-06
Hi everybody.
I need to know if there is a way of obtaining the code necessary to do the exact same as double click a file(in other words execute).
It is not a very usual file it is the executable for urban terror 64bit version.
I need the code cause glc asks me.
If it is a nautilus script better(hehe).
Thanks.

---

### Post by taurus on 2009-02-06
If you want to run something from a prompt (terminal), first make sure it has an executable permission and then you just run it, assuming you are in the directory where that file is.

```
chmod +x *filename*
./*filename*
```

---

### Post by billgoldberg on 2009-02-06
Make sure the executable has the correct permissions.

Then in a terminal

/path/to/executable

---

### Post by 569874123 on 2009-02-06
Thanks.

---

