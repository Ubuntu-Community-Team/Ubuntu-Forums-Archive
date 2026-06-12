---
title: "Cannot open trash, here's a screenshot"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-01
Trash content could not be viewed

---

### Post by Truefire on 2010-02-01
For some reason, it looks like it's trying to open trash as root..

No idea what's going on here.

---

### Post by Ubunser on 2010-02-01
> **Truefire said:**
> For some reason, it looks like it's trying to open trash as root..

No idea what's going on here.

This is because I tried to access it as root as my last resort as accessing it as user gave same results

---

### Post by Ubunser on 2010-02-01
Can I cd to trash via terminal or through file system? Trash has acumulated some good size by this time which is taking place. Soo... I need to force open it

---

### Post by Gatemaze on 2010-02-01
it might be a problem with permissions... an easy way of maybe testing that things work is to create a new user, log on as the new user and try to see what is happening with the trash...

---

### Post by chaanakya_chiraag on 2010-02-01
Yes, you can cd to Trash:
```
cd ~/.local/share/Trash/files
rm -rf *
```
CLARIFICATION: The second line will **delete all of the files in Trash**

---

### Post by Ubunser on 2010-02-01
> **Gatemaze said:**
> it might be a problem with permissions... an easy way of maybe testing that things work is to create a new user, log on as the new user and try to see what is happening with the trash...

I created a new user, but it let me in a completely new systmem, where trash is empty. Moreover it required logging in as previous user to view hdd contents

---

### Post by Ubunser on 2010-02-01
> **chaanakya_chiraag said:**
> Yes, you can cd to Trash:
```
cd ~/.local/share/Trash/files
rm -rf *
```
CLARIFICATION: The second line will **delete all of the files in Trash**

Yes I cleared trash this way, but can I find a way to do it grapgical interface next time?

---

### Post by no2498 on 2010-02-01
just thinking try getting rid of the cache first then temp files

---

### Post by Ubunser on 2010-02-01
> **no2498 said:**
> just thinking try getting rid of the cache first then temp files

If I understood you right I just cleared firefox and opera cash and temp folder, the last preserving though several files.

---

### Post by chaanakya_chiraag on 2010-02-01
To delete trash files graphically, just browse to ~/.local/share/Trash/files using Nautilus (you may have to "Show Hidden Files" by pressing Ctrl-H or going to View->Show Hidden Files).  If you want quick access, just create a bookmark by pressing Ctrl-D or Bookmarks->Add Bookmark.

---

