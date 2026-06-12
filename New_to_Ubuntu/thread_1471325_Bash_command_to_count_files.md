---
title: "Bash command to count files ?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by nnjond on 2010-05-03
Hi,
Can you help me please?

I would like to count all the jpgs in my home folder

I need a command like this:

~$ Sudo count -R /*/*.jpg

Thanks

---

### Post by mathfreak123 on 2010-05-03
I would think something like....

```

find -name *.jpg | nl

```

might work?

---

### Post by Seal Daemon on 2010-05-03
```
find $HOME -name *.jpeg | wc -l
```

---

