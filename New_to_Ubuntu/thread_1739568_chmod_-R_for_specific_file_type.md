---
title: "chmod -R for specific file type"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by SilverbugNZ on 2011-04-26
Hi all,

I just read in this thread that you can change the permissions of all files/folders using -R, but can you specify to only change the permissions of specific file types?

[http://ubuntuforums.org/showthread.php?t=492186](http://ubuntuforums.org/showthread.php?t=492186)

ie. I have a bunch of .swf files in different folders i want to change the permissions to 664

i would have thought chmod -R 664 *.swf would have worked but it seems it doesnt

Cheers

---

### Post by lmarmisa on 2011-04-26
Welcome to the forums.  

Try this command:  ```
 find . -name '*.swf' -exec chmod 664 {} \; 
```

---

