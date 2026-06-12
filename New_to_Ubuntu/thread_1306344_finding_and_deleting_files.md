---
title: "finding and deleting files"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by ahmedeleven on 2009-10-30
i just want to remove more than file with the same name from a specific mounted partition

i wrote 

```
 #find /media/[mounted partition] -name [filename] 
```and don't know how to remove the files from the output

---

### Post by SuperSonic4 on 2009-10-30
```
find /path/to/dir -type f -name "*filename" -exec rm -f {} \; 
```



Source: [http://ubuntuforums.org/showpost.php?p=1257361&postcount=2](http://ubuntuforums.org/showpost.php?p=1257361&postcount=2)

---

### Post by ahmedeleven on 2009-10-30
thanks .. it worked :)
but can u explain how did it work ?

---

### Post by sisco311 on 2009-10-30
well, you can use the delete option of the find command:
```
find /media/[mounted partition] -type f -name [filename] -delete
```

or you can move the files to the trash:

```
find /media/[mounted partition] -type f -name [filename] -exec trash '{}' \;
```

you can list the content of the trash with:
```
list-trash
```

restore the files with:
```
restore-trash
```

empty the trash with:
```
empty-trash
```

you may have to install the trash-cli package first:
```
sudo apt-get install trash-cli
```

---

### Post by ahmedeleven on 2009-10-30
got it :) .. thanks for helping me :)

---

### Post by sisco311 on 2009-10-30
```
man find | less --pattern\="\-exec command"
```

-exec = execute a command
{} is replaced by the file name.

EDIT: 
> **ahmedeleven said:**
> got it :) .. thanks for helping me :)

oh, okay!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

