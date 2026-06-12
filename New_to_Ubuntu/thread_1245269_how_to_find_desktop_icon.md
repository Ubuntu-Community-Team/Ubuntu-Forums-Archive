---
title: "how to find desktop icon?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by garyed on 2009-08-20
There are tons of icons on my computer running Hardy. 
Some in usr/share/pixmaps some in usr/share/icons & probably a lot of other places I don't know about too. What I'm trying to do is find exactly what files are associated with my existing desktop icons so if I change them it won't take me forever to get them back. The only thing I've found to do is right click on the desktop icon then click properties & then click on the icon which just brings up the file system to search for a new icon. It doesn't show where the existing icon is located or its file name.  
Any ideas?

---

### Post by philinux on 2009-08-20
No need. If you select properties and then click the icon the window that opens has a Revert button. i.e. revert to original.

---

### Post by alexlafreniere on 2009-08-20
Wait, you want to replace the desktop icon for an application with a custom one? I would go into the terminal and issue this command:

```
whereis <your_app>
```

This will tell you possible locations of where that app is installed. This folder also likely contains resources for that application, i.e. the icon you're looking for. Hope this helped.

---

### Post by garyed on 2009-08-20
Thanks for the answers, they both helped.
I'm a little surprised though that there is no sure way to locate the exact file that is currently being used for the icon.

---

### Post by CatKiller on 2009-08-20
> **garyed said:**
> I'm a little surprised though that there is no sure way to locate the exact file that is currently being used for the icon.

The easiest way is to drag-and-drop your launcher to a text editor. [.desktop files]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec") are just text files.

---

### Post by jrox717 on 2009-08-20
>  The easiest way is to drag-and-drop your launcher to a text editor. .desktop files are just text files. 

That doesn't work for me using gedit... I just get error messages like 

>  /home/jennifer/Desktop/flash_drive is a directory. 
Please check that you typed the location correctly and try again.

---

