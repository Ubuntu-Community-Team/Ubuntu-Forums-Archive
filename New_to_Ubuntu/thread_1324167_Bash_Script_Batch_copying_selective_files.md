---
title: "Bash Script: Batch copying selective files"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Igniteflow on 2009-11-12
Hi,
I have a directory with multiple subdirectories, all containing multiple images.  Could someone help me with a bash script or terminal command to copy all the files containing "_407" in the file name to a new directory, while maintaining the original directory structure??  
Hope that makes sense.

---

### Post by kaibob on 2009-11-12
> **Igniteflow said:**
> Hi,
I have a directory with multiple subdirectories, all containing multiple images.  Could someone help me with a bash script or terminal command to copy all the files containing "_407" in the file name to a new directory, while maintaining the original directory structure??  
Hope that makes sense.

I believe the following will do what you want. I tested it with a few files and it worked OK. You need to change the source and target directories. 

```
#!/bin/bash

source="/home/kaibob/"
target="/home/kaibob/test"

find "$source" -name '*_407*' -type f | while read file ; do
   path="${file%/*}"
   mkdir -p "${target}${path}"
   cp "$file" "${target}${path}"
done
```

---

