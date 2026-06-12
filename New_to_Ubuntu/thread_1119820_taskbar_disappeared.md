---
title: "taskbar disappeared"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by gkraju on 2009-04-08
hi i am using ubuntu 8.04 
my taskbar disappeared 
how to recover it 
please help

---

### Post by Lunx on 2009-04-08
I'm assuming you still have one panel still showing? Right click on it and you'll see an option to add **new panel**. Right click on the new panel that appears and you'll see that you can select **add to panel** which will give you choices as to what you want to place on it

---

### Post by gkraju on 2009-04-08
> **Lunx said:**
> I'm assuming you still have one panel still showing? Right click on it and you'll see an option to add **new panel**. Right click on the new panel that appears and you'll see that you can select **add to panel** which will give you choices as to what you want to place on it

no 
no panel is visible 
what should  i do

---

### Post by Jakey_TheSnake on 2009-04-08
Open a terminal (Applications > Accessories > Terminal), try:

```
gnome-panel
```

If that doesn't work, you'll have to create a new panel (taskbar) as stated above. If you want to add any launchers and don't know how, post here and I will respond =) 

And this time, after you've done it, run: 

```
sudo apt-get install gconftool-2
```

After that's installed:

```
gconftool-2 --dump /apps/panel > ~/ubuntu.entries
```

This will save your panel setup, you can restore it in future with:

```
## loads settings into gconf
  gconftool-2 --load ~/ubuntu.entries
## kills the gnome-panel so it restarts with the new gconf settings
  killall gnome-panel
## restart gnome network monitor applet which dies after killall gnome-panel
  nm-applet &
```

---

### Post by gkraju on 2009-04-08
> **Jakey_TheSnake said:**
> Open a terminal (Applications > Accessories > Terminal), try:

```
gnome-panel
```

If that doesn't work, you'll have to create a new panel (taskbar) as stated above. If you want to add any launchers and don't know how, post here and I will respond =) 

And this time, after you've done it, run: 

```
sudo apt-get install gconftool-2
```

After that's installed:

```
gconftool-2 --dump /apps/panel > ~/ubuntu.entries
```

This will save your panel setup, you can restore it in future with:

```
## loads settings into gconf
  gconftool-2 --load ~/ubuntu.entries
## kills the gnome-panel so it restarts with the new gconf settings
  killall gnome-panel
## restart gnome network monitor applet which dies after killall gnome-panel
  nm-applet &
```

how to go to terminal 
there is nothing (Application ,etc are all disappeared )
i dont know how to go to terminal
i opened web browser by just opening a file in the disk
help please

---

### Post by matrixblue on 2009-04-08
Press Alt-F2 then type gnome-panel then click run.

---

### Post by neu2buntu on 2009-04-08
press keys:-- "alt f2" together and type in "terminal"

---

### Post by starcannon on 2009-04-08
Open a terminal by:

[LIST=1]
[*]Press Alt+F2
[*]Type gnome-terminal
[/LIST]
You can also reset the panels with:
```
sudo dpkg-reconfigure gnome-panel
```GL and have fun.
You may have to reboot to see changes take affect.

---

### Post by gkraju on 2009-04-08
> **starcannon said:**
> Open a terminal by:

[LIST=1]
[*]Press Alt+F2
[*]Type gnome-terminal
[/LIST]
You can also reset the panels with:
```
sudo dpkg-reconfigure gnome-panel
```GL and have fun.
You may have to reboot to see changes take affect.

Alt +F2 not working(no window opened)

---

### Post by Lunx on 2009-04-08
> **gkraju said:**
> how to go to terminal 
there is nothing (Application ,etc are all disappeared )
i dont know how to go to terminal
i opened web browser by just opening a file in the disk
help please

hit** Ctrl + Alt + F2 **and that will open a terminal for you.

when finished you can type *exit* to escape back to your desktop in GUI 

Ctrl + Alt + F7 will also bring you back in the same way as *exit* will

---

