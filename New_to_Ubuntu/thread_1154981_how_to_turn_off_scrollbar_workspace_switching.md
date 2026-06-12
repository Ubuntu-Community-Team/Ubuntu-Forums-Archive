---
title: "how to turn off scrollbar workspace switching?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by sportscrazed2 on 2009-05-10
anyone know how to do it?  please help me out it's the worst feature in ubuntu as far as i'm concerned

---

### Post by Eberhard on 2009-05-10
Alt+F2 -> "gconf-editor"

Goto: apps->compiz->plugins->vpswitch->allscreens->options

Change the value of next_button and prev_button to "Disabled"

Don't know if this changes anything else but this should solve your problem.

---

### Post by cholericfun on 2009-05-10
hi

i like the scroll feature - just wondering if one could somehow tell it to switch between the 2 workspaces by scrolling in EITHER direction

---

### Post by Eberhard on 2009-05-10
> **cholericfun said:**
> hi

i like the scroll feature - just wondering if one could somehow tell it to switch between the 2 workspaces by scrolling in EITHER direction

I'm running Ubuntu 9.04 and if I use two workspaces I can change between them by either scrolling up or down. Are you running compiz? If so, what are your values for "next_button" and "prev_button"?

---

### Post by Dex73 on 2009-05-10
> **Eberhard said:**
> Alt+F2 -> "gconf-editor"

Goto: apps->compiz->plugins->vpswitch->allscreens->options

Change the value of next_button and prev_button to "Disabled"

Don't know if this changes anything else but this should solve your problem.

This worked for me. Just type "Disabled" for next and previous button.

---

### Post by cholericfun on 2009-05-10
> **Eberhard said:**
> I'm running Ubuntu 9.04 and if I use two workspaces I can change between them by either scrolling up or down. Are you running compiz? If so, what are your values for "next_button" and "prev_button"?

i'm on an 8.04

next and previous button are Button4 / 5
i can change by rolling up or down but say from WS1 i scroll UP to WS2
but from WS2 i can't scroll UP to WS1 ...
not much of a hassle - just takes an extra second but thought there might be a quick change to do that would fix it..
as in 
can i have 2 values for the next_button / prev._button
thanks

---

### Post by Dex73 on 2009-05-10
I had that problem too. Make sure to click one of the other options after typing "Disabled" or it will assume that you don't want to save your changes. Also set my keyboard shortcuts for workspace switching to Ctrl left arrow and Ctrl right arrow under System/Preferences/Keyboard Shortcuts.

---

