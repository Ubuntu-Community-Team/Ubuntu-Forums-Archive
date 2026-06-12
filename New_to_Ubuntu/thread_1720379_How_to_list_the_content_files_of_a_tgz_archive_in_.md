---
title: "How to list the content files of a tgz archive in terminal?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Zombir on 2011-04-03
Hi,
Can somebody please tell me a command that will list the contents in a .rar compressed files in the terminal of Ubuntu? I've been searching for such a command for a while now. Everybdoy suggests me to use the Archive Manager but I want a way to display it in terminal with a terminal command! 

Please help!!!

Thanks

---

### Post by sisco311 on 2011-04-03
```
rar l archive.rar
```

If you install [atool]("http://packages.ubuntu.com/maverick/atool"), you can use als:
```
als archive
```
or
```
atool -l archive
```

---

### Post by Zombir on 2011-04-03
Thanks that will do.

---

