---
title: "Kmenu update?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by mmitt on 2009-01-29
Whenever I install a new app, it doesn't automatically update the Kmenu. Is there a way for it to automatically update itself with whatever has been downloaded from adept? If not, how can I launch an app from terminal so that I can manually add items to the menu? Thanks!

---

### Post by yeats on 2009-01-29
You should be able to right click on the menu and select Menu Editor.  There will be an icon to click and create a new menu item, then you can name it and define the command to bring the program up (which would be the command you use in the terminal).

Most of the time the terminal command is simply the name of the program (i.e., "firefox"), but if you've installed your program in a directory that is not in your command path (which is a terminal environment variable that you can see the contents of by doing

```
echo $PATH
```

in your terminal to see which directories are being searched), you might have to do something like 

```
/opt/openoffice3/soffice
```

to get the program started.

If that's not clear, post back and maybe I or someone else can help.

---

### Post by mmitt on 2009-01-29
Thats ok i got it. If you just hit "save" in edit k menu, it auto updates. Thanks though.

---

