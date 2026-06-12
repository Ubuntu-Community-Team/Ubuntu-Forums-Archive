---
title: "How to get permission to create folders and files"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by thorbs on 2010-06-10
I have installed lampp on my computer and want to create folder and files in the www folder. But I do not have permission to this. I have been reading around but can not find out how to get permission. 
According to the Ubuntu wiki I should just be able to go to file and properties on the folder and there choose permissions. But there is not a properti possibillity on the lampp (var and www) folders.

---

### Post by cbecker78 on 2010-06-10
I could be wrong as I haven't done this, but I think you want to open a terminal and type ```
sudo chown your_user_name /var/www/
```
You may want to wait for some other opinions though

---

### Post by limestone on 2010-06-10
sudo chown -R username /path/to/dir

ex: Changing owner of folder "new" at your desktop (sudo chown -R username /home/username/desktop/new

---

### Post by rsmitty on 2010-06-10
I like to use Alt+F2 and then type 'gksudo nautilus'. That gives root permissions to run Nautilus. I just prefer this way because i find it easier to use the GUI to create folders and drag/drop files and whatnot. I guess you still may need to use 'chown' though in order to edit the files.

---

### Post by thorbs on 2010-06-10
Thanks that worked...

---

