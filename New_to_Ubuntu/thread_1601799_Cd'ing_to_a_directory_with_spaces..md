---
title: "Cd'ing to a directory with spaces."
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Jetso on 2010-10-20
I'm am trying to cd to my Program Files on my C:/ using the terminal. When I type in ```
cd Program Files
``` it says that there is not directory called "Program" This is obviously because that it has a space. What do I do to access the file without changing the name?

---

### Post by sandyd on 2010-10-20
> **Jetso said:**
> I'm am trying to cd to my Program Files on my C:/ using the terminal. When I type in ```
cd Program Files
``` it says that there is not directory called "Program" This is obviously because that it has a space. What do I do to access the file without changing the name?

use double quotes
i.e.
```

cd "Program Files"
```

---

### Post by luvshines on 2010-10-20
You can escape the spaces with \
```
cd Program\ Files

## Or simply put the directory names in ""
cd "Program Files"
```

---

### Post by CharlesA on 2010-10-20
You can use quotes or use "\" before the spaces (or just use tab completion, which is what I do)

cd Program\ Files

cd Prog <tab>

---

### Post by Jetso on 2010-10-20
There we go! That worked!

---

