---
title: "pin applications in dockbarx??"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-10-16
how do i do this?

---

### Post by kerry_s on 2010-10-16
you can "right click-> pin" when used
or
drag & drop from the menu to the dock

---

### Post by owners4life5 on 2010-10-16
> **kerry_s said:**
> you can "right click-> pin" when used

my initial thought anyway, still no go ):

> or drag & drop from the menu to the dock

tried this, didn.t work.

---

### Post by kerry_s on 2010-10-16
you sure your using dockbarx & not dockbar ?

---

### Post by owners4life5 on 2010-10-16
yeah in the 'add to panel' list it.s referred to as 'DockBarX Applet'

---

### Post by M7S on 2010-10-16
Something is seriously wrong if you can't drag-drop from the gnome-menu (note that it doesn't work with  gnomenu or cardapio or other menus, it has to be the normal gnome-menu) to dockbarx (you have to drop it on a group button, not on the handle or something like that) to make pin an application.

Try running dockbarx in window to see if you get any error messages.
In a terminal write:
```
dockbarx_factory.py run-in-window
```and copy-paste the output here.

---

### Post by owners4life5 on 2010-10-16
```
brian@brian-gateway:~$ dockbarx_factory.py run-in-window
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:706: Unable to find include file: "apps/gnome-panel.rc.bak"

** (dockbarx_factory.py:3451): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3451): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3451): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
dockbar init
/usr/bin/dockbarx.py:802: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in pixbuf.get_pixels_array():
/usr/bin/dockbarx.py:850: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in pixbuf.get_pixels_array():

```

ran that, and now it works fine?
weird

---

### Post by AndyM3 on 2010-10-16
Miracles do happen.
You may want to mark the thread solved now that you've fixed this, so others can find the fix if they have the same problem. ;)

Off-topic: thanks to M7S for this great app! Better than any other dock I tried and completely Mono-free! :D

---

