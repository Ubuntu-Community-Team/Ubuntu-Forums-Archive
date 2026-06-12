---
title: "permissions and eclipse workbench"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by danfangdango on 2010-05-28
Hi,

I've recently changed to Ubuntu and have begun developing applications. I have downloaded Eclipse and I wish to set my workbench as var/www, but I don't have permission to do so.

I have opened the terminal and logged on as root **sudo username** and can navigate to the var/www folder and make new directories **mkdir**, however I can't do this in the graahical interface i.e, right click and add foler and when I once again try and set my eclipse work bench to var/www, I can't. 

Do I have to set permissions for the graphical interface, too?

I hope this message is clear to people and that someone will be kind enough to help.

Kind regards

---

### Post by diafanos on 2010-05-28
Hello danfangdango.

You can run nautilus as root: Press Alt+F2 and write
```

gksu nautilus

```

then go to the folder you want to access and change the permissions so that everyone can read and write to these folders

---

### Post by danfangdango on 2010-05-30
Thank you very much for your help.

---

