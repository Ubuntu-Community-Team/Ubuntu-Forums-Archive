---
title: "Gnomenu: Error,File not found."
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Sriram137 on 2010-07-15
Here is the problem.I installed GnoMenu.It installed perfectly.
Then i tried to add it to AWN,the applet wasnt workin.

So i tried 

```
GnoMenu.py run-in-window
```

in terminal and got this error.

```
tart
shaping window
Traceback (most recent call last):
  File "/usr/lib/gnomenu/GnoMenu.py", line 246, in map_event
    self.hwg = Main_Menu(self.HideMenu)
  File "/usr/lib/gnomenu/Menu_Main.py", line 88, in __init__
    self.setup()
  File "/usr/lib/gnomenu/Menu_Main.py", line 340, in setup
    self.PGL = IconProgramList()
  File "/usr/lib/gnomenu/Menu_Widgets.py", line 1845, in __init__
    self.XDG = XDGMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 113, in __init__
    self.Restart(item)
  File "/usr/lib/gnomenu/Menu_Items.py", line 155, in Restart
    self.ConstructMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 261, in ConstructMenu
    self.addtomenu(_("Menu editor"),"alacarte",6,"","alacarte")
  File "/usr/lib/gnomenu/Menu_Items.py", line 186, in addtomenu
    self.L_Icons.append(self.IconFactory.geticonfile(icons))
  File "/usr/lib/gnomenu/IconFactory.py", line 121, in geticonfile
    pix = self.gtkicontheme.load_icon(icon,Globals.PG_iconsize,gtk.ICON_LOOKUP_FORCE_SIZE)
gio.Error: Error opening file: Permission denied

```

Can anyone help?

---

### Post by pettsium on 2010-11-25
I'm getting the exact same error. Any solution to this problem? Strange thing is is that I can run using sudo GnoMenu.py run-in-tray. If I try this command without sudo I get the error that was reported by the OP

---

