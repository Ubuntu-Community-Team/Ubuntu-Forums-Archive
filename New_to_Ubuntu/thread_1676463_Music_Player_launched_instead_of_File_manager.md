---
title: "Music Player launched instead of File manager"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by irvken on 2011-01-27
Ubuntu 10.10 Every time I try to access my folders from the Places menu it has started to launch a Music player!! I can launch nautilus from the command line and use it but I'd rather fix this menu problem.

---

### Post by amsterdamharu on 2011-01-27
I am not sure where the settings for this are, could you post the output of the following command?

```
ls /etc/udev/rules.d/
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code]```
Your pasted stuff
```&#91;/code]

---

### Post by Frogs Hair on 2011-01-27
Here is another option to change the default application for opening folders.

[http://ubuntuforums.org/showthread.php?p=10316525#post10316525](http://ubuntuforums.org/showthread.php?p=10316525#post10316525)

---

### Post by amsterdamharu on 2011-01-27
Frogs Hair is right, I was mistaken with inserting USB media.

> Right click the desktop and select create folder . Right click the  folder and select open with another application . Select file browser  from the menu and make sure remember this application is checked. Remove  the folder when finished.  

The default application for opening home folders was somehow changed to appearance preferences.

Just change the application that will open folders as posted before:

---

