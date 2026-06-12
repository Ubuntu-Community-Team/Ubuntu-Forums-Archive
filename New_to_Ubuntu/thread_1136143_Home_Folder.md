---
title: "Home Folder"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-04-24
When I go to Places-Home Folder a Movie player Panel opens up.
This is crazy.
Can anyone help?

---

### Post by RichardLinx on 2009-04-24
You're /home folder is probably automatically set to open up the wrong application when you click it. Locate the folder (Computer > File System > Home > /home) then right click and select properties and in the "open with" tab select it to open with "Open Folder". If that is the issue it should fix it.

---

### Post by llamabr on 2009-04-24
if not, post the output of 

```
ls -lh /home/
```

---

### Post by bigal1932flying on 2009-04-24
Could not see any "open With" tab.
Output of command is:
total 4.0K
drwxr-xr-x 74 afrancis afrancis 4.0K 2009-04-25 13:39 afrancis
Thanks.

---

