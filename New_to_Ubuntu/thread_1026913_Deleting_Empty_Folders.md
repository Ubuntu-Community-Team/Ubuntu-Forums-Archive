---
title: "Deleting Empty Folders"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Limitlesschannels on 2008-12-31
Heya

I am fairly bad at shell scripting and need a quick script to delete all empty folders.  Could someone please help me with this?  In some cases I have empty folders within other folders, but running the script twice can probably just take care of that.
  I searched for this and got a couple jumbled threads, but if I wasn't looking in the right place a friendly point in another direction would be equally helpful.

---

### Post by taurus on 2008-12-31
For a single empty directory,

```
rmdir directory_name
```
For directory that has more directories under it,

```
rm -rf directory_name
```

---

### Post by fubbleskag on 2008-12-31
[http://www.cyberciti.biz/faq/linux-unix-shell-check-if-directory-empty/](http://www.cyberciti.biz/faq/linux-unix-shell-check-if-directory-empty/)

---

### Post by Limitlesschannels on 2008-12-31
My folder hierarchy is much more complex than just deleting one folder.  I have many folders under one.  Some of the folders have content and others are blank.  There are a couple hundred, however, and I really dont want to go through them all manually.

---

