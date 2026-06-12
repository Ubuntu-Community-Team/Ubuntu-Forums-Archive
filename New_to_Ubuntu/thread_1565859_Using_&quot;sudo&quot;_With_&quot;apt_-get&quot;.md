---
title: "Using &quot;sudo&quot; With &quot;apt -get&quot;"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by YUbnyEjczqPdLOKKXKTq on 2010-09-01
Is there ever a time when you wouldn't use "apt -get" with "sudo"?

---

### Post by andrewthomas on 2010-09-01
To simulate an upgrade 

```
apt-get upgrade -s
```

---

### Post by da burger on 2010-09-01
Well there are ways of using apt get without typing ```
sudo apt-get
``` but the idea is always the same. Essentially apt-get modifies system files and therefore it needs permission to do this. sudo grants it that permission. In practice on ubuntu there is no reason to use apt-get without sudo.

EDIT I didn't think of dry-runs. Even then you should probably run those as root to ensure the command would run in the exact same way.

---

