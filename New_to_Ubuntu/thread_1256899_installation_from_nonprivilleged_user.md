---
title: "installation from nonprivilleged user?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by minsf on 2009-09-03
hi,
i have two users on my system: user1 and user2.
user1 is a sudoer, so she can install a package with "sudo apt-get install packageName". no prob.
however, i would like user2 to install a program, but not become a sudoer. obviously, user2 is not allowed to make changes to the entire system, but i would still like her to install a package for her own use.
how does she do it?

---

### Post by neurostu on 2009-09-03
Packages cannot be installed for local use. They are only installed globally. If you want to install a program locally you should download it from source and compile it.

When you run configure (if the package uses autotools), use the following command:
```

./configure --prefix=/home/$USER/compiled_programs/

```
this will ensure that thethe program will only be installed locally when you run:
```

make install

```

---

