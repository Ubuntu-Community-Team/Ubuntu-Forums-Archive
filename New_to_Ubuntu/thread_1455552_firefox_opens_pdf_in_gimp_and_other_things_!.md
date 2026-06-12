---
title: "firefox opens pdf in gimp and other things !"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by medya on 2010-04-16
I use latest ubuntu 9.10 and latest firefox,
whenever I download a pdf , when I double click on it, it opens it in GIMP, and it opens other stuff in more stupid softwares .

is there any way to reset it to whatever it was at first ?

I keep manually changing PDF to be opened in document viewer but it changes everytime it is really annoying

---

### Post by ed-koala on 2010-04-16
Yup.  In Firefox go to Edit - Preferences - Applications tab.  Find the type of file you want and change which app is associated with it.  Everything should work as you want then.

---

### Post by medya on 2010-04-16
I know that dude, but all the default application been changed by something ,i didnt change it bymself and when I change it back to what it was, it keeps gettinb back to gimp, is there any simple way to reset it for all by one click?

---

### Post by lovinglinux on 2010-04-16
Close Firefox and move the file **mimeTypes.rdf ** from your FF profile (~/.mozilla/firefox/<profilename>) to a backup folder. Start Firefox again. This should reset the options. When you try to open a pdf file again, it will prompt for what application you want to use.

---

