---
title: "Applications menu won't open"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by coolcalt on 2009-01-14
I have two users installed, and for one of them, the Applications menu will not open and I can't start the menu editor.

I believe the menu editor can be started by 'alacarte' which results in the following output  

```
calvin@Q1LNX10:~$ alacarte
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
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
```

I deleted all entries from ~/.local/share/applications which had no effect.

Its seems from the stacktrace that there is a node missing in one of the config files, but I have no idea which one or where they might be.

I'm running gnome with ubuntu 8.04, with all updates.

Any help is appreciated.

---

### Post by drs305 on 2009-01-14
alacarte is listed in synaptic. have you tried reinstalling it?

---

### Post by coolcalt on 2009-01-21
yes, I have reinstalled it using synaptic, with no joy.

I'll expand my description of the problem more explicitly; I'm running 8.04 ubuntu.  While do have some KDE apps installed, I run Gnome window manager.  I think I may have cancelled an update while it was downloading files, and to my surprise it still went to the installing... dialog instead of just quitting.  This may not be the cause, It is interesting none the less, and my situation unchanged.  That is that only one of my users can't access the Applications tab at the top of the screen.  Places and System still work aok.  Clicking on Applications shows a little dot in the bottom left of the button, but no menu, and the dot is seemingly unfunctional.

So I'm trying to debug the issue.  It seems to be a user configuration issue.  I found the location of the extra menu items when this issue first started, which escapes me at the moment, and deleted all the files found there, to no effect.  

So where is Accessories, Games, Programming, System, Other, Internet etc defined?  This is what I want to look at next.

---

### Post by coolcalt on 2009-01-21
ok Issue Solved

I copied .config/menus/applications.menu from my other user and it started working!

Thanks for your help

I got my clue from

[http://ubuntuforums.org/showthread.php?t=790562](http://ubuntuforums.org/showthread.php?t=790562)

---

### Post by jkorten on 2009-01-25
This bug seems to appear when the editing process for the "applications" menu craps out.

In my case I had run a disk imaging program and didn't know it imaged my partition TO my partition and I filled up my disk drive.

Then I went and tried to edit the "applications" button by right clicking on applications and selecitng "Edit Menus" and the thing crapped out and I didn't have any more applications.

Fortunately the "places" button still works. Do the following: select places->home folder. Then select "view" from the menu and click on the "show hidden files" check box. Then scroll down until you see the directory ".config" and double click on this directory and you will see a "menus" directory under that. Double click on the "menus" directory. Right click on the file named "applicatoins.menu" and rename it to "old.applications.menu" and then close the file browser window.

The system magically rebuilds the applications menu (?!) and you can now access your applications again.

Hope this helps too.

Regards,


Jerry

---

