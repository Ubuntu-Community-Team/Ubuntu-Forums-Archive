---
title: "Taskbar Missing from desktop area"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by yahyanoorani on 2009-10-20
Hello Gurus,

I am a new user, I am using ubuntu 8+ unknowingly few keystrokes got pressed resulted  taskbar missing from desktop area. I cannot find nor I can execute any programs. I tried with novice know how but not fortunate :confused:.
I appreciate if I could get any help to resolve it, thanks for your efforts and contribution.

Cheers
yahyanoorani

---

### Post by martrn on 2009-10-20
hit <alt> + <f2>  type in gnome-panel

this should launch your gnome panels if they have been stopped for some reason.

---

### Post by yahyanoorani on 2009-10-20
It does not work, I can move on the desktop screen area the pointer only.

---

### Post by martrn on 2009-10-20
<alt> + <f2> should work,

but if it doesn't right click on an area of the desktop and create a launcher.  

type ```
gconf-editor
``` in the command section, and double click.

and make sure you have an entry  'top level.

if your gnome settings are that messed up just delete the .gconf .gnome .gnome2 and other gnome temporary directories from your /home/username directory and reboot.

You should be able to right click an area of your desktop to crate a launcher to any program even though you have no panels.

---

