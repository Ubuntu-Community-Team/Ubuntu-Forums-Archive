---
title: "help with script"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by ozzyprv on 2010-07-31
This is probably a silly (and lazy) question.

Could anybody help me with a script top change file names from 2010July01_IMG_abcd.jpg to 20100701_IMG_abcd.jpg?

I want to do this for a lot of files at the same time. The day (01) and the number "abcd" would change from file to file.

Thanks.

---

### Post by TeoBigusGeekus on 2010-07-31
I'd do it with Bulk Rename.

---

### Post by satman-ga on 2010-07-31
```
#!/usr/bin/python
import shutil
import glob
files = glob.glob('*.jpg')
for line in files:
        shutil.move(line,line.replace('July','07'))
```

---

