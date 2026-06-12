---
title: "Folder access"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by servicetech on 2009-05-14
I have some folders I moved from a Windows PC to my Linux PC and the folders show "nobody" as the owner. Of course I can't modify the files since "nobody" owns them. is there a way I can change ownership of the file?

---

### Post by AndThenWhat on 2009-05-14
Yes. Press ALT+F2 and in the box that pops up type "gksu nautilus". Then hit ENTER. Put in your password and then a file browser will come up with root privileges meaning you have permission to edit anything. From there you need to navigate to the files and right-click them and go to the permissions tab.

---

### Post by servicetech on 2009-05-14
Worked perfect :)
Thanks.

---

