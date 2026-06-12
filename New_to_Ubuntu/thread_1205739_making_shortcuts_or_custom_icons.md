---
title: "making shortcuts or custom icons"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Barky on 2009-07-06
I've been using Ubuntu since last may, and have had this problem ever since then. I cannot make shortcuts in Ubuntu, they simply fail every time. I've settled by just writing a bash script and putting them on the desktop for the programs I want shortcuts for, seems to work fine. However, they are quite ugly looking icons and would rather have the icons from the programs themselves.

making a "Launcher" for me never worked, the games I tried with it just crashed on startup, saying the files were missing. From the code it looked like the program was looking for the files in the current directory of the shell script, which is the desktop :/ ... 

So if anyone could help me with this shortcut issue or just tell me how to set custom icons to bash scripts I would appreciate it

---

### Post by cph05a on 2009-07-06
If you right click on the icon and click edit (it might be called properties, I don't have my comp with me) there is an option for changing the icon. You can set the command it runs to whatever script you want it to run as well.

---

### Post by Celauran on 2009-07-06
> **Barky said:**
> I cannot make shortcuts in Ubuntu, they simply fail every time.

So dragging icons from the Applications menu to the desktop doesn't work? Does it generate any errors?

Desktop shortcuts in GNOME are .desktop files, so you may want to [look at this](http://standards.freedesktop.org/desktop-entry-spec/latest/apa.html).

---

### Post by Barky on 2009-07-07
> **Celauran said:**
> So dragging icons from the Applications menu to the desktop doesn't work? Does it generate any errors?

Desktop shortcuts in GNOME are .desktop files, so you may want to [look at this](http://standards.freedesktop.org/desktop-entry-spec/latest/apa.html).

The things I want to link are not from the applications menu. they are to .sh files usually.

---

### Post by Tyke91 on 2009-07-07
what happens when you open a terminal, cd to the directory the script is in and type this command
```
ln -s YourfileName ShortcutName
```

---

### Post by CatKiller on 2009-07-07
> **Barky said:**
> making a "Launcher" for me never worked, the games I tried with it just crashed on startup, saying the files were missing.

There is a Path property for .desktop files. You can read all about them in the link that Celauran gave you.

---

