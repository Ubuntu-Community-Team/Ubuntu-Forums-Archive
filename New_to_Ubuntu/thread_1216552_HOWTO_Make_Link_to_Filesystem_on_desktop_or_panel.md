---
title: "HOWTO: Make Link to Filesystem on desktop or panel"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by markoid8 on 2009-07-18
You may have noticed that there is no way to make a link to the filesystem, not even as root.

You can easily create a launcher to do this on your desktop, or panel.

To do so, follow these instructions:

Right click on your desktop, and click 'Create Launcher...'
In the 'Name' field, type whatever title you want. I used 'Filesystem'.
In the 'Command' field, type without the quotes: 'nautilus /'
You can add a comment if you wish.

You can click on the icon to change it to any image on your computer.
If you want the icon to have the same functionality and resize-ability of other drive icons, follow the steps below:

Open 'Text Editor' [also known as gedit]
Drag the icon into the window. You can also open the launcher file from within gedit.
gedit will now display the script that makes up the icon.

Where it says 'Icon='
Change it to, without the quotes: 'Icon=harddrive'

Then save the file.

And that is it.
You can drag the launcher to the panel, or create it in the panel.
This technique can be used to open any directory.

Simply change the '/' after the nautilus command to the directory of choice, such as '/media'

This will also work with other file browsers other than nautilus.

---

### Post by llamakc on 2009-07-18
> **markoid8 said:**
> You may have noticed that there is no way to make a link to the filesystem, not even as root.


Yes there is.

```
cd ~/Desktop && sudo ln -sf / Filesystem
```

---

### Post by hugmenot on 2009-07-19
Just try dragging with middle click. Creates symlink. Problem solved.

---

