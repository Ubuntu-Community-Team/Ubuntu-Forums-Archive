---
title: "Application menu gone and &quot;Main menu&quot; isn't accessible"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by ALF102 on 2010-09-28
While I was trying to sort things up in menu using Main Menu from Preference>Main Menu, the program got stuck. So I just close it, but when I try to re-open it, it won't open. Then I realize "Application" is gone from my Gnome Main Menu.

---

### Post by wojox on 2010-09-28
Have you tried right clicking and +Adding to panel?

---

### Post by Paqman on 2010-09-28
Also, you can re-open the Main Menu editor by hitting Alt-F2 and typing:
```
alacarte
```

This should allow you to sort out any mess that it's got into.

---

### Post by ALF102 on 2010-09-28
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 48, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0


now what?


PS:Running alacarte in Alt+F2 doesn't do anything

---

### Post by ALF102 on 2010-09-28
ok, it seems I found the file named alacarte in usr/bin/. I manage to get the menu editor open but the thing is when I open the menu editor, it seems like everything is just fine...but then why can't I open the menu editor normally in Preference>Main Menu? 
    I also checked out the folder Alacarte in usr/lib/pymodules/python2.6, so here are some files that I found. I don't know if these files have any problem or not.

---

### Post by Land Rover Series 3 on 2010-09-29
I don't know if this is anything to do with it or not, but the item "gnome-panel" has to be in the menu (accessories I think) otherwise the panel itself won't appear. It can be hidden though (unchecked). Found this out from experience ;-)

---

### Post by ALF102 on 2010-09-29
ok, it doesn't work. Somehow I remember of modifying a keyboard shortcut to the Application menu..you know, pressing the Window logo on the keyboard and then Application menu comes down

---

### Post by keroman on 2010-09-29
This may assist you

[http://ubuntuforums.org/showthread.php?t=1526755](http://ubuntuforums.org/showthread.php?t=1526755)

:)

---

### Post by ALF102 on 2010-09-29
Well, I did that and both my top and bottom panel is re-appearing...but the main thing is the application menu (the one in between the ubuntu logo and Places) is still gone. I mean, it says there "Application" but when I click it, theres no drop down menus.  When I used my AWN to click on the Gnome main menu, the whole part of the menu with Accesseries, Games, Graphics, Sounds and Videos, Software Centre, etc...is gone. But when I re-checked the alacarte file, it shows that all of those is checked.

---

### Post by keroman on 2010-09-30
had a look around and found this similar post, may help

[http://ubuntuforums.org/showthread.php?t=1372033&highlight=application+menu+problem](http://ubuntuforums.org/showthread.php?t=1372033&highlight=application+menu+problem)

---

### Post by wojox on 2010-10-01
Open your terminal and try resetting this way

```
rm -rf .gconf/apps/panel
```

---

### Post by ALF102 on 2010-10-01
Uhm...Now that I've done a thorough check, I have this feeling the problem isn't originated from Panel settings or something similar. But anyway, thank you for spending time helping. I'm gonna make a system reset anyway...due to....unavoidable circumstances.

---

### Post by migs73 on 2010-10-01
> **ALF102 said:**
> Uhm...Now that I've done a thorough check, I have this feeling the problem isn't originated from Panel settings or something similar. But anyway, thank you for spending time helping. I'm gonna make a system reset anyway...due to....unavoidable circumstances.

Oooops! :-?

---

