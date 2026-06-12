---
title: "My main menu deleted itself!"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by VinisLentoje on 2009-08-21
Hello,
Opened System -> Preferences -> Main Menu; unchecked a couple of no longer used shortcuts of windows programs installed with wine, and bang! all the folders in the main menu vanished. The main menu program seemed to be "dead" as it did not respond to any mouse-clicks. I killed it. Tried running it again. but nothing happened. Then I tried running it in the terminal, and I got this:

```
vinis@g44:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/dist-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/dist-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/dist-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

So, right now, I have an empty main menu, and i can't run the program to manage it.
Can someone help me?
Thank You in advance.

---

### Post by VinisLentoje on 2009-08-22
B.ring
U.p
M.y
P.ost

---

### Post by realzippy on 2009-08-22
what happens,if you delete the broken mainmenu,and add a new one?

(rightclick on panel delete/add,mainmenu)

---

### Post by drs305 on 2009-08-22
If you can see the main menu icon, try right click, Edit Menus, Revert to restore the original menu. Or is that dead too?

---

### Post by Copernicus1234 on 2009-08-22
> **VinisLentoje said:**
> B.ring
U.p
M.y
P.ost

That was pretty original. :)

---

### Post by andru183 on 2009-08-22
although i know this isnt the best fix but instead of the main menu bar i use a thing call screenlets and it has a wiget style menu that may fix your prob, i dont understand if all the programs are gone or just the menu selection of em but this mite help till you get a proper answer

---

### Post by VinisLentoje on 2009-08-23
> **realzippy said:**
> what happens,if you delete the broken mainmenu,and add a new one?

(rightclick on panel delete/add,mainmenu)

Gives the same empty main menu


> **drs305 said:**
> If you can see the main menu icon, try right click, Edit Menus, Revert to restore the original menu. Or is that dead too?

when I click "edit menus" nothing happens. I think is suppose to be launching the same main menu management program, that, as i already wrote, no longer starting for me (terminal output in the first post)


-----
Also, note: only the first section of my main menu is empty, that "programs" one, the "places" and "system" sections are in tact (since i use a Lithuanian version, i do not remember the English names of those sections)

---

### Post by drs305 on 2009-08-23
Have you tried reinstalling alacarte? In Synaptic, highlight, right click, and mark for reinstallation; or
```

sudo apt-get install --reinstall alacarte

```

In addition to restoring alacarte the reinstall will rewrite the python 2.6 library *.py scripts that are producing some of the errors.

---

### Post by hansdown on 2009-08-23
Hi VinisLentoje.

Not sure if I'm misunderstanding you, but if you open main menu, on the left side, click preferences. Make sure main menu is checked.

---

### Post by VinisLentoje on 2009-08-23
> **drs305 said:**
> Have you tried reinstalling alacarte? In Synaptic, highlight, right click, and mark for reinstallation; or
```

sudo apt-get install --reinstall alacarte

```

In addition to restoring alacarte the reinstall will rewrite the python 2.6 library *.py scripts that are producing some of the errors.

Tried reinstalling like You said, in various ways, but it did not help, that program still won't start. (Same terminal output, as it was before, if I try to run it in the terminal)

> **hansdown said:**
> Hi VinisLentoje.

Not sure if I'm misunderstanding you, but if you open main menu, on the left side, click preferences. Make sure main menu is checked.

As I already wrote, i can't run this main menu management program, it won't start/crashes. (once again, terminal output can be found on the 1st post)

---

### Post by Liolikas on 2009-08-23
Submit bug to Ubuntu bugzila. They probably fix it with update.

---

### Post by drs305 on 2009-08-23
I've already sent the OP a PM regarding bugs. There is one filed here:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97449]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97449")

I don't know if it applies or not (which was the reason for the PM). In any case, two of the topics reported in the bug thread were a lack of space in the partition and also that deleting $HOME/.config/menus sometimes corrected the problem (although I would suggest renaming rather than deleting the folder).

---

### Post by VinisLentoje on 2009-08-23
> **drs305 said:**
> I've already sent the OP a PM regarding bugs. There is one filed here:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97449]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97449")

I don't know if it applies or not (which was the reason for the PM). In any case, two of the topics reported in the bug thread were a lack of space in the partition and also that deleting $HOME/.config/menus sometimes corrected the problem (although I would suggest renaming rather than deleting the folder).


Well, my Home directory was far from being full with only 9% used.
But renaming the  $HOME/.config/menus solved the problem!

Thank You VERY much!

---

### Post by VinisLentoje on 2009-08-23
It happened again.
I have noticed that it happens when I try to uncheck a link that has some strange characters (screenshot included).

---

### Post by hackerseraph on 2009-08-23
Do you know when that garbled menu entry first appeared or after what program inspired that entry?

---

### Post by VinisLentoje on 2009-08-23
> **hackerseraph said:**
> Do you know when that garbled menu entry first appeared or after what program inspired that entry?

I think that is one of my old wine applications, I had a couple of game cds with a russian locale, it must be one of those.

If someone would tell me where all those shortcuts are kept (i once found that dir, but don't remember where), I would delete all the unwanted shortcuts for good, since i had accumulated over 100 of unwanted ones.

EDIT: found that dir and deleted all the unwanted shortcuts.

---

