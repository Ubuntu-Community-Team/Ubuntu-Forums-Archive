---
title: "thunar won't let me delete a few files from trash"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-01-19
Greetings,

This is a minor issue, but I am unable to delete a few files from my Trash.  I tried to compile ZSNES from source, it failed, so i moved the entire folder to trash.

When I tried to empty the trash, I cannot delete:

/zsnes_1_51/src/autom4te.cache/output.0
/zsnes_1_51/src/autom4te.cache/output.1
/zsnes_1_51/src/autom4te.cache/requests
/zsnes_1_51/src/autom4te.cache/traces.0
/zsnes_1_51/src/autom4te.cache/traces.1

I get Permission Denied errors.

How can I remove those files?

Thanks,
Redmage913

PS: Xubuntu 9.04 if anyone needs that info.

---

### Post by sisco311 on 2010-01-19
How did you try to compile the application? You shouldn't compile as root.

Anyway, change the owner of the files:
```
sudo chown -R $USER\: ~/.local/share/Trash/
```
then try to empty the trash.

---

### Post by Redmage913 on 2010-01-19
perfect!  thanks a lot!

However, my trash icon won't change to the 'empty trashcan' type icon now.

---

### Post by Redmage913 on 2010-01-19
Correction: I logged out and back in and it's fine.  Thanks so much!

---

