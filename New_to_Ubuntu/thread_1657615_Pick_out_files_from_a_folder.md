---
title: "Pick out files from a folder"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by rkakkar on 2011-01-01
i have a text file full of filenames. I want to pull out those files from a folder containing those plus a whole lotta other files, and put it in another folder. How can I do so?

---

### Post by TeoBigusGeekus on 2011-01-01
Something like
```
#!/bin/bash
for i in $(cat /path/to/list/with/filenames/list
do
mv $i /path/to/new/location/
done
```

---

### Post by sisco311 on 2011-01-01
> **TeoBigusGeekus said:**
> Something like
```
#!/bin/bash
for i in $(cat /path/to/list/with/filenames/list
do
mv $i /path/to/new/location/
done
```

This will fail if the files have spaces in their name or their name begins with a -

Try:
```

cd path/to/dir/with/files
while read file; do
  mv -b -- "$file" path/to/new/location/
done < path/to/list/with/filenames/list
```

---

### Post by TeoBigusGeekus on 2011-01-01
> **sisco311 said:**
> This will fail if the files have spaces in their name or their name begins with a -


^ This...

---

