---
title: "where do i put .so file"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by sinista on 2010-10-14
Hi, 

Ive just converted from windows so be honest I haven't got a clue what I'm doing, I'm working on a Java app that would need a .dll file to be placed in the windows folder, but as far as i can tell i need a .so file for Ubuntu, so my question is where do i put the file?  

Thanks in advance :)

---

### Post by sandyd on 2010-10-14
> **sinista said:**
> Hi, 

Ive just converted from windows so be honest I haven't got a clue what I'm doing, I'm working on a Java app that would need a .dll file to be placed in the windows folder, but as far as i can tell i need a .so file for Ubuntu, so my question is where do i put the file?  

Thanks in advance :)
32bit
```

gksudo nautilus /usr/lib

```
64bit
```

gksudo nautilus /usr/lib64
```
drag n drop

---

### Post by sinista on 2010-10-14
brilliant thanks very much

---

### Post by dalekirkwood on 2011-02-08
Brilliant, been looking for that command for a long time

---

