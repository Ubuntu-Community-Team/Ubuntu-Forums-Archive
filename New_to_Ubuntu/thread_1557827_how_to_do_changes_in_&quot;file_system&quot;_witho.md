---
title: "how to do changes in &quot;file system&quot; without password"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-08-21
i want to edit copy in this linux files. is there any way to access this part without using terminal password.

---

### Post by jakupl on 2010-08-21
> **munna.cheyur said:**
> i want to edit copy in this linux files. is there any way to access this part without using terminal password.

in terminal, do:

```
sudo -s
```

That will give you temporary super-user privileges in the terminal, until you close it, or type in, "exit".

---

