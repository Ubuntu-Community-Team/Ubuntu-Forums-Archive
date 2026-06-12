---
title: "Root Group"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by yangt299 on 2009-04-26
Hi all I would like to make myself part of the root group, and then allow every user that is in the Root group to be able to access and edit all the files on the computer, including those in the file system. I know that this is insecure, and have read the comments of many other people saying how insecure this is, so I needn't be told this again. I have successfully added my user to the Root group (system --> administration --> users and groups, then click on manage groups and added myself to the root group) but I do not know how to allow the root group to edit and view all the files on the entire computer. Thanks and again please no comments about how insecure this is. Thanks!

---

### Post by wizard10000 on 2009-04-26
I don't think you're gonna find anybody in here who'll help you bypass Ubuntu's security protocols.  If you don't know how to do it then you shouldn't be doing it  ;)

---

### Post by unutbu on 2009-04-26
Making yourself part of the root group will not allow you to edit root files.

For example, look at /etc/fstab:
```

  -rw-r--r--   1 root root      1780 2009-04-26 09:31 fstab

```
The default permissions only allows the root user to write to /etc/fstab.
Being part of the root group only allows you to read the file.

A better solution is to create a convenient menu item or launcher to run "gksu nautilus".
This will launch the nautilus file browser with root privileges. Then you could navigate to any file, double click it, and if it is a text file, it will open in your default text editor.

---

### Post by yangt299 on 2009-04-26
Are there any instructions on how to do this? Thanks again!

---

### Post by unutbu on 2009-04-26
Well to make a menu item, click System>Pref>Main Menu.

In the left panel, click "Accessories". In the far right column, click the "New Item" button. Enter

```
Name: Root file browser     # or any name you like
Command: gksu nautilus
```

Click Ok.
Click Close.

Now test it out by clicking Applications>Accessories>Root file browser.

---

### Post by yangt299 on 2009-04-27
Thanks so much, this is just what I've been looking for.

---

### Post by ibuclaw on 2009-04-27
> **yangt299 said:**
> Thanks so much, this is just what I've been looking for.
Remember, with power comes responsibility. If you are using your system properly, you won't need to use it most the time. ;)

Regards
Iain

---

