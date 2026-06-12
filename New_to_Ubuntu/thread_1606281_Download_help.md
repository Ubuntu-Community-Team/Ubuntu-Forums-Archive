---
title: "Download help"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by zharless92 on 2010-10-26
Is it possible while using 'apt-get install' to save the package i'm downloading to use later?

---

### Post by alexandari on 2010-10-26
*deleted*

---

### Post by Paddy Landau on 2010-10-26
If you need to know more about a command, use the "man" command:
```
man apt-get
```You'll see that you can use the --download-only option.

Example:
```
sudo apt-get --download-only install openshot
```This will download the package. Later, to install, you can use:
```
sudo apt-get install openshot
```

---

### Post by lavinog on 2010-10-26
It also works for updates.
```

sudo apt-get update;sudo apt-get -dy dist-upgrade

```

The y tells it to do it without asking...do **NOT** use it if you are not using the download-only option (-d for short)

---

