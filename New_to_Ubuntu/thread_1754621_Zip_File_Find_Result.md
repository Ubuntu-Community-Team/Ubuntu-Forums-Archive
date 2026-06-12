---
title: "Zip File Find Result"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Kakym on 2011-05-10
I want to transfer todays updated/new files to a folder named Archive which is achieved as follows:

find . -iname "*" -mtime 0 -exec cp {} ~/Archive \;

Is it possible to incorporate a command to zip the resulting files into the above terminal entry?

Thanks

---

### Post by TeoBigusGeekus on 2011-05-10
You could create a script
```
#!/bin/bash
find . -iname "*" -mtime 0 -exec cp "{}" ~/Archive \;
zip backup.zip ~/Archive/*
```

---

### Post by Kakym on 2011-05-11
Thanks

I'll experiment with scripts

---

