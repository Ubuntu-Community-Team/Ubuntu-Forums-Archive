---
title: "Tray icons restore"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by milanfcb on 2010-06-21
OK.. Sometimes I do something stupid.. Like I did this time..
I accidently clicked right click-->remove panel (right upper corner) on Network Connections and Pidgin.. and now I don't know how to get it back :S
I set on Pidgin to always show icon on tray, but it's still not there...
When I use Add to Panel, I can only set to tray executable program.. Like Network Connections, when I click it, it opens settings, and I want that "wireless" icon..
Help, plz..
I'm using Lucid Lynx..

---

### Post by wojox on 2010-06-21
open a terminal and run these two commands

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel


```

---

### Post by philinux on 2010-06-21
What you did was remove the "Notification Area" applet.

Add that one back where you want it.

---

### Post by milanfcb on 2010-06-21
It worked! :)
Tnx a lot guys...

---

