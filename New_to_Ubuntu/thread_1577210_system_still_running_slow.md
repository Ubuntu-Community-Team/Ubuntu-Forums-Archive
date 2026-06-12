---
title: "system still running slow"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by mike101 on 2010-09-18
Hello

I'm fairly new to Ubuntu.

I've having trouble with everything running quite slow. I think it may be something to do with my file system. I seem to have all
of my files appearing on the desktop. The files go home/mike/   
with everything in mike being on the desktop (seems to be that desktop=mike). I've tried moving the contents of mike directly into the home folder ( so its home/second folder) but I need to use  a root command for this. Any ideas as to what happened most welcome.

---

### Post by ibuclaw on 2010-09-18
Somehow, you've set Home == Desktop in the gnome config settings.

Open gconf-editor - you can press **Alt+F2** and type/paste it into the run command box
```
gconf-editor
```
Navigate to:
```
/apps/nautilus/preferences
```
And look for the key
```
desktop_is_home_dir
```
Uncheck it, then logout / login again.

Regards

---

### Post by mike101 on 2010-09-18
Hello

The home=desktop option was unchecked.  I think my personal folder mike =desktop not the home folder. Is there any way I could have done that? How can I undo it?

Cheers

---

### Post by Old_Grey_Wolf on 2010-09-18
Did you delete the /Mike/Desktop folder? I deleted my Desktop folder once. :)

---

