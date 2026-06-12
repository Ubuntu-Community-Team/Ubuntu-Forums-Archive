---
title: "How do I reset 'Places' links"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by jamesdonaldson on 2011-02-18
Hello

I have some bizarre behaviour with Maverick. On the top panel, under 'Places', I have the usual Home etc folders listed. If I click on Home Folder then I get the splash screen of Open Office 3.2 which quickly disappears and nautilus fails to show. Similar behaviour for Desktop through to Downloads on the default menu. If I click on 'Computer' then nautilus loads and the file structure is shown as expected.

If I remove Open Office then the Places menu works as expected bringing up Nautilus.

If I then reinstall OpenOffice the problem reappears.

Any clues as to what is happening?... better still, how to fix it?

---

### Post by yeats on 2011-02-18
try installing alacarte:

```
sudo apt-get install alacarte
```

This will put a new item in System -> Administration -> Preferences named "Main Menu".  You can select the items that are not working correctly and click Properties to see what command is being executed by each.

---

### Post by nick_goodfate on 2011-02-18
[http://ubuntuforums.org/showthread.php?t=1687671](http://ubuntuforums.org/showthread.php?t=1687671)
Same problem there solved

---

### Post by jamesdonaldson on 2011-02-18
Alacarte is already installed and the latest version. The problem is with the links underlying the top menu items under 'Places'.

How do I set the link for 'Home Folder' to load nautilus and show the folder?

---

### Post by nick_goodfate on 2011-02-18
In case you didn't saw the link i gave you ... 
Use [Ubuntu tweak]("http://ubuntu-tweak.com/")

---

### Post by Frogs Hair on 2011-02-18
Reset default application for opening places folders.[http://ubuntuforums.org/showthread.php?p=10316525#post10316525](http://ubuntuforums.org/showthread.php?p=10316525#post10316525)

---

