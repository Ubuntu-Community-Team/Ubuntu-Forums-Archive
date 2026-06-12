---
title: "How to make deb install launcher in Accessories menu?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by bilalakhtar on 2009-12-13
I have a deb that installs a .desktop file in the /usr/share/applications folder. But, when I install the deb, the launcher appears in the Other menu, not the Accessories menu. Which line should I change in this file?
```

[Desktop Entry]
Encoding=UTF-8
Name=BCalc
Comment= A simple calculator
Exec=/usr/bin/bcalc
Terminal=false
Type=Application
Categories=Calculator; Application;
StartupNotify=false
```

---

### Post by mikewhatever on 2009-12-13
I am not quite sure, but having looked at some of the .desktop items residing in Accessories by default, it looks like the 'Category=' line determines where the launcher is placed in the menu.
Example:
/usr/share/applications/gnome-terminal.desktop
```
Categories=GNOME;GTK;Utility;TerminalEmulator;

```

/usr/share/applications/gcalctool.desktop
```
Categories=GNOME;GTK;Utility;Calculator

```

/usr/share/applications/gedit.desktop
```
Categories=GNOME;GTK;Utility;TextEditor;

```

In short, I think 'Utility' is the key word your might be looking for.

---

### Post by bilalakhtar on 2009-12-14
Thank you very much. It worked! The utility line was missing.:popcorn:

---

