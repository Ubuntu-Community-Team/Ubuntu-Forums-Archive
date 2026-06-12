---
title: "New Folder"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by rawbertb on 2011-06-27
How do I create a new folder in my Home Folder?

---

### Post by _0R10N on 2011-06-27
```
mkdir ~/MY_NEW_FOLDER
```

or via Nautilus

Right Click on Home Folder -> Create New Folder ->Type MY_NEW_FOLDER

---

### Post by honeybear on 2011-06-27
```
dest=$(zenity --entry --title "Hi guy" --text "Folder name"  --entry-text "" ) ; echo "You entered: $dest"
[ "$dest" = "" ] && exit
cd  ; mkdir "$dest"

```

---

### Post by rawbertb on 2011-06-27
When I right click, all I see is "Home Folder" and "Keep In Launcher"

---

### Post by Morbius1 on 2011-06-27
Click the Home folder to open Nautilus. Right Click on an empty space and select : Create Folder.

If you have Nautilus set up to display a list instead of icons:
Hover your mouse over the top panel and some words magically appear. One of them should be "FIle". Select that and then select "Create Folder".

[I]Warning- Mini Rant: Providing assistance for people running Ubuntu with Unity is going to be a real trip. "Hover your mouse over the top panel ... ". Is this any way to run a railroad.

[/I]

---

### Post by grahammechanical on 2011-06-27
Try right clicking the desktop. When the desktop loads under your user name you are automatically put into the home folder. So, any folder you create will be in the home folder. That is why the folder icon in the Launcher that you are right clicking on is called Home Folder.

Regards.

---

### Post by cogier on 2011-06-27
All the above is no doubt correct but can I suggest that if Nautilus is showing your **Home **folder just press **[Ctrl] + [Shift] + N** and your new folder will appear.

---

