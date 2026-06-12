---
title: "Gnome panels top and bottom gone"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by willywonder86 on 2009-04-03
Hi

Big problem I seem to have lost my top and bottom panels and cannot get them back any help would be great.

---

### Post by ibuclaw on 2009-04-03
Hi, are you still having this problem?

To restore your panel back to normal (the way it was defaulted to when you first installed ubuntu), press **Alt+F2** and type in
```
gnome-terminal
```

The following should reset it and bring back the panels:
```
gconftool -recursive-unset /apps/panel
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

Then close, and press **Alt+Ctrl+Backspace** to restart X and log back in.

Regards
Iain

---

### Post by willywonder86 on 2009-04-04
Still have the problem the alt+f2 to open a run application box does nothing no popup window. The only reason I am still able to use ubuntu is with loads of launchers on the desktop.

---

### Post by willywonder86 on 2009-04-04
Created a launcher for terminal and tried the above gives me error see below

Error while parsing options: Unknown option -recursive-unset.
Run 'gconftool --help' to see a full list of available command line options.

---

### Post by Phospholipid on 2009-04-04
Do you still have this problem? 
I had the same thing yesterday.

I ran a terminal and used
```
killall gnome-panel
```
which told me the panel wasn't running
I then did 
```
gnome-panel
```
to run it which worked successfully.

I then added gnome-panel to the session so that it would always be run with the desktop.

---

### Post by willywonder86 on 2009-04-04
okay tried killall gnome-panel I get a report of

gnome-panel: no process killed

when I type gnome-panel this message pops up

Gtk:ERROR:/build/buildd/gtk+2.0-2.14.4/gtk/gtkrecentmanager.c:1933:get_icon_fallback: assertion failed: (retval != NULL)
Aborted

Not sure what all that means but to me looks like the icon package I installed is causing the problem.

---

### Post by ibuclaw on 2009-04-04
Hi, sorry about that,

it is:
```
gconftool --recursive-unset /apps/panel
```

Not **-recursive-unset** as I previously stated.

Regards
Iain

---

### Post by willywonder86 on 2009-04-05
Thanks for the help that seems to have done the trick.

---

### Post by yildiz.a on 2009-04-14
Thanks for help!

---

