---
title: "how can i remove directory-file (Using CLI)..?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-12
[SIZE=2][COLOR=Black][I]how can i remove directory-file (Using CLI)..?

e.g i made a directory(name=me) on the desktop  and now i want to delete this using terminal,so how i can do it?
i have tried to use "rm" to remove this but it shows "cant remove,because it is a directory.

thnkx[/I][/COLOR][/SIZE]

---

### Post by philinux on 2010-09-12
> **tajiknomi said:**
> [COLOR=Black][SIZE=3][I][B]how can i remove directory-file (Using CLI)..?

e.g i made a directory(name=me) on the desktop  and now i want to delete this using terminal,so how i can do it?
i have tried to use "rm" to remove this but it shows "cant remove,because it is a directory.

thnkx
[/B][/I][/SIZE][/COLOR]

```
man rmdir
```

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by kamicc on 2010-09-12
You should use 

```

rm -R dir_name

```

instead :)

It is Recursive Removing Mode ;)

---

### Post by RJ12 on 2010-09-12
I usually just do

```
rm -rf directoryname
```

---

