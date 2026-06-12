---
title: "[SOLVED] chmod questions"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by sarc on 2008-12-31
How can I chmod 777 a folder and its contents to make it available for read/write to all users?

I tried launching nautilus as root (sudo nautilus) then changing the file permissions BUT IT DOES NOT WORK!  Sometimes the permissions stay unchanged and sometimes they change to something else.  Thanks!

---

### Post by mikewhatever on 2008-12-31
sudo chmod -R 777 /path-to-folder

Warning: Don't run it on /home or any system folder because you'll then be in trouble.

---

### Post by joseangelini on 2008-12-31
in a console do:

sudo chmod -R 777 folder/


Good luck

---

### Post by Michael.Godawski on 2008-12-31
if you are using nautilus as root start it with

```
gksudo nautilus
```

usually it is:

```
sudo chmod -R 777 /foldername_or_directory
```

---

### Post by sarc on 2008-12-31
Thanks guys!

---

