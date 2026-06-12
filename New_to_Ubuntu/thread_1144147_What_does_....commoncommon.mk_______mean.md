---
title: "What does ../../common/common.mk       mean?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by newport_j on 2009-04-30
What does the statement mean:

include ../../common/common.mk


I know what 

cd ..

means, but I am unsure of this other one. I need to know because I am resetting some makefiles after an NVIDIA installation. I just need to what it means.

Thanks in advance.

Newport_j

---

### Post by kanikilu on 2009-04-30
```
cd ../ # one directory up from current
cd ../../ # two directories up
cd ../../../ # three directories up
# and so on
```

---

### Post by decoherence on 2009-04-30
kanikilu is correct. in plain english you read 

include ../../common/common.mk

as "include the file 'common.mk' which is in the directory 'common' which is in the parent directory of the parent directory of the current directory"

clear as mud! ;)

---

### Post by newport_j on 2009-05-01
What does the statement mean:

include ../../common/common.mk


I know what 

cd ..

means, but I am unsure of this other one. I need to know because I am resetting some makefiles after an NVIDIA installation. I just need to what it means.


Now I know that  .. means to go to the parent directory, but what does ../../ mean?


Go to the parent of the parent? They talk about this in the Ubuntu Pocket Guide on pages 73 - 74 when Frank moves from the pictures to the music folder; and it seems to be on a whole new directory tree! Please explain this.

Thanks in advance.

Newport_j

---

### Post by original_jamingrit on 2009-05-01
You're right, ../../ is the parent of a parent.

If, for example you are in the directory ```
/home/pete/play
```, then typing in the command: ```
cd ../../julie/work
``` will change the directory to ```
/home/julie/work
```, when you are using most normal shell commands.  ".." always means parent, "../.." is parent of a parent, "../../.." is parent of a parent of a parent, and so on.

And that's just the tip of the iceberg, as far as nifty shell tricks go.

---

### Post by kanikilu on 2009-05-01
> **newport_j said:**
> What does the statement mean:

include ../../common/common.mk


I know what 

cd ..

means, but I am unsure of this other one. I need to know because I am resetting some makefiles after an NVIDIA installation. I just need to what it means.


Now I know that  .. means to go to the parent directory, but what does ../../ mean?


Go to the parent of the parent? They talk about this in the Ubuntu Pocket Guide on pages 73 - 74 when Frank moves from the pictures to the music folder; and it seems to be on a whole new directory tree! Please explain this.

Thanks in advance.

Newport_j

Why the [duplicate thread]("http://ubuntuforums.org/showthread.php?t=1144147")?

// Edit, nevermind, it appears they've been merged :)

---

