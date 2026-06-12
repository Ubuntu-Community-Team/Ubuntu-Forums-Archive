---
title: "Linux source code documentation"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by SteelCore on 2009-08-12
Where is it possible to download the source code for Linux in addition to the official documentation that could help the reader understand it.  Many thanx.

---

### Post by 3rdalbum on 2009-08-12
For the Linux kernel, or for all the programs and packages that make up Ubuntu?

If you want the source code of any package in Ubuntu, you can type this:

```
sudo apt-get source packagename
```

(where "packagename" is the exact name of the package you want the source for - you need to have the Source Code repository enabled too). The source code will go into /usr/src, I believe.

If you want the source code for the latest Linux kernel releases, you can visit [www.kernel.org](www.kernel.org), and if you want some help understanding it you can visit [www.kernelnewbies.org](www.kernelnewbies.org).

---

