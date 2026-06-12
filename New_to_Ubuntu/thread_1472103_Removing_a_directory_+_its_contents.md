---
title: "Removing a directory + its contents"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by iggy pop on 2010-05-04
Have been learning how to remove/delete a directory + it's contents which i created for this purpose but failed at each attempt. Have been using: 

$ rmdir NewOne

But i keep getting the following response:

Failed to remove 'NewOne' : Directory not empty

Would someone tell me what i am doing wrong please.

---

### Post by jbrown96 on 2010-05-04
```
rm -rf PATH
``` ```
man rm
```

---

### Post by v1ad on 2010-05-04
rm
-r stands for recursive and deletes everything in folder and all
-f forcefully removes it without asking permission to remove anything it just does it. 
so rm -r foldername
rmdir only removes empty folders

---

### Post by iggy pop on 2010-05-04
Finally succeeded using: rm -rf PATH. Thanks for the replies and help both.

---

