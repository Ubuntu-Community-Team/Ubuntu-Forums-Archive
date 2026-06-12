---
title: "AAAAARGH! applications menu suddenly empty ..."
date: 2009-05-12
forum: New to Ubuntu
---

### Post by pmooney78 on 2009-05-12
I crashed my computer while editing the applications menu earlier tonight. Now there is nothing in the applications menu at all ... I click on it and a tiny square (maybe two or three pixels on a side) appears at the lower-left side, as if it were trying to drop something down but the menu is empty. I can start some programs from a terminal (or with ctrl+F2), but it's inconvenient not to have the menu there ...

Right-clicking on the menu and choosing "Edit Menus" doesn't do anything. (Nothing at all ... no error message, nothing.) My "Places" and "System" menus are intact.

Any help would be much appreciated.

---

### Post by Viva on 2009-05-12
Did you try removing the applet and readding it?

---

### Post by pmooney78 on 2009-05-12
Yes ... no dice ... still empty. 

Thank you for the quick reply!

---

### Post by Flimm on 2009-05-12
Open a terminal and type```
alacarte
```alacarte is the program that is run when you click 'Edit Menus'. Tell us what you get here.

---

### Post by Viva on 2009-05-12
Is the "Gnome Main Menu" Applet working?

---

### Post by pmooney78 on 2009-05-12
I get this:

```

patrick@liniscient:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 24, column 67
patrick@liniscient:~$

```

---

### Post by pmooney78 on 2009-05-12
> **Viva said:**
> Is the "Gnome Main Menu" Applet working?

I've never used it before, so it's hard to say. I added it and get a menu that gives me the standard Preferences and Administration menus from the system menu, plus Lock Screen, Log Out, and Shut Down ...

Not sure if there's supposed to be something else in there ...

---

### Post by pmooney78 on 2009-05-13
Problem solved. I opened up Synaptic, searched installed packages for "menu", and looked at what files each one solved. I ran likely-looking programs that were installed under /usr/bin and /usr/sbin until I stumbled on gmenu-simple-editor, which showed all options unchecked. Checking (almost) everything brought the menus back. Running alacarte from a terminal now works and reports no problems. :)

---

