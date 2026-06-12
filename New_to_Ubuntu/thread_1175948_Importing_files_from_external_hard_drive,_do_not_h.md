---
title: "Importing files from external hard drive, do not have significant permission"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by cnc6670 on 2009-06-01
[FONT=Times New Roman][SIZE=3]Hello everyone,[/SIZE][/FONT][FONT=Times New Roman][SIZE=3] this is my second day on Ubuntu, and I apologize in advance if this is in the wrong section or if there's another thread about this.

I hooked up my external G-Drive to my computer to import my music and pictures. However, when I open the folders those files are in, it says that I do not have significant permission to view those files. How do I change this?

Thanks.
[/SIZE][/FONT]

---

### Post by mapes12 on 2009-06-02
You could try accessing the files in nautilus with root permissions. In Terminal ```
gksudo nautilus
``` then drag and drop them to your home/user folder. This guide will give you more info on permissions and changing them: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

