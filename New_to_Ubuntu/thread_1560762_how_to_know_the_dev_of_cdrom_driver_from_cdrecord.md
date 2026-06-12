---
title: "how to know the dev of cdrom driver from cdrecord ?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by honeybear on 2010-08-25
Hello 

I found on internet this command that indicates the drive info; but how to get it saying /dev/hdc from the cdrecord atip command ?

```
drive=$(cdrecord -atip  2>&1)  ; echo $selection | while read i ; do echo "$i" ; done
```

---

### Post by honeybear on 2010-08-25
Solved !

```
wodim --devices | grep  dev= | cut -f1 | cut -d"=" -f2  | sed s/\'//g | tail -n 1 
```

---

