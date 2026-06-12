---
title: "Password protecting directories"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Eisenwinter on 2009-03-13
I don't really know about password-protecting, but you can change the permissions for a directory so nobody except root (for example) can view and add contents in it.

```
chmod -R 007 /path/to/directory
```

This command will enable root-only reading, writing, and executing in the directory.

---

### Post by binbash on 2009-03-13
you can encrypt the folder with truecrypt

---

