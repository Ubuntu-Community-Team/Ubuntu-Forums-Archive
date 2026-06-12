---
title: "Desktop dosen't show any files or folders"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Falc7 on 2010-10-05
Strange thing, the my desktop has some files on there, and i can see them when i use nautilus, but when i am viewing the desktop normally, there is nothing there. Additionally, right clicking on the desktop dosen't bring up the normal menu of create new folder ect

---

### Post by Clever_Username on 2010-10-05
I wonder if Nautilus is showing you hidden files. Are you running Nautilus as root?

---

### Post by Falc7 on 2010-10-06
Nope the files on the desktop are not hidden, not running nautilus as root

---

### Post by Peter09 on 2010-10-06
There is a setting - but I am not at my machine to find it - which sets nautilus to show desktop files on the desktop.

---

### Post by fatality_uk on 2010-10-06
> **Falc7 said:**
> Strange thing, the my desktop has some files on there, and i can see them when i use nautilus, but when i am viewing the desktop normally, there is nothing there. Additionally, right clicking on the desktop dosen't bring up the normal menu of create new folder ect

Try running the following in a terminal:

```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type boolean true
```

See if it brings back your icons?

---

### Post by eakron on 2010-10-06
The fact that you can't right click the desktop implies that Nautilus is not drawing it. Is your wallpaper working?

---

### Post by Falc7 on 2010-10-06
> **fatality_uk said:**
> Try running the following in a terminal:

```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type boolean true
```

See if it brings back your icons?

Thats it, thanks!

---

### Post by nikefalcon on 2010-10-06
Please mark thread as solved.

---

