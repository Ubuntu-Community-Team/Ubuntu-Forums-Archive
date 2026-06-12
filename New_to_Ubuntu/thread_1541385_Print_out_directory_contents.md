---
title: "Print out directory contents"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by gallifrey on 2010-07-29
Hi all, 
       I have a drive with 120 directories, each containing a large number of sub-directories, and a vast number of files. I need a hard copy of this drive's contents for various purposes, i.e. Directory, all files and subdirectories it contains, and all files in the subdirectories, listed in their locations, and was wondering how to go about it, short of copying and pasting everything manually. 

Any suggestions??

---

### Post by nothingspecial on 2010-07-29
The -R flag will make ls output subdiectories which you can output to a text file

```
ls -R /path/to/parent/directory > file.txt
```

Now you can open file.txt with gedit or abiword etc and print it

or just ```
lpr file.txt
```

---

### Post by wallaroo on 2010-07-29
The 'tree' command will give you a few more options for producing a more usable listing.
You can pipe the output to a file or printer if needed.

For example to produce a nice indented tree listing use ...
    ```
tree -a
```or to produce a simple recursive list of files with full pathnames use ...
    ```
tree -fai
```

---

### Post by ghostdog74 on 2010-07-29
ls -R, tree and find command all can do directory listing. Also, the bash shell

```

#!/bin/bash
#bash 4.0

shopt -s globstar
for file in **/*
do 
  echo "$file"
done

```

---

