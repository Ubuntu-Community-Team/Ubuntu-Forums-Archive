---
title: "Nautilus hangs on reading certain directories"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Statik on 2009-11-23
Hi all,
I've noticed this occurring on two fresh installs of 9.10. When opening some directories, usually containing movie files, nautilus seems to get stuck. The menus and tree seem to work fine, but the contents of that folder are not displayed and the little 'working' mouse pointer is displayed. CPU doesn't seem to be working hard and no amount of time makes the content appear. I managed to make some appear by using the terminal and renaming the files, Each file I renamed appears in the browser window as soon as its renamed.

Most of these files were moved to the computer via thumb drive or samba, but some were bitorrent downloads. Any ideas?

Statik

---

### Post by ukripper on 2009-11-23
You can try using Thunar instead and see whether it solves your problem. Thunar is very fast - [http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html](http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html)

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

If you want to stick to nautilus then let's troubleshoot the problem.
can you post output of the following command after when nautilus freezes:```
tail -n 100 /var/log/messages
```

---

