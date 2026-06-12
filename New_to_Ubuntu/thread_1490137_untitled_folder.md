---
title: "untitled folder"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by hduguay on 2010-05-21
I was trying to open terminal by using shift control N and now on my desktop I have untitled folder which I cannot remove. Can anybody help me with this ? I am using 10.04.

---

### Post by Zyrtec on 2010-05-21
Go through System -> Preferences -> Keyboard Shortcuts and then go to Desktop -> Run a Terminal. Set it to whatever shortcut you want.

As for your untitled folder, as long as there's nothing important in it, do this at terminal:

```
cd Desktop
sudo rmdir untitled\ folder

```

---

