---
title: "Alt Tab not working"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by vigneshmw on 2011-06-18
hi, let me explain my query

i am using a ubuntu system and connecting to ***windows*** remote desktop. i login to citrix throgh citrix receiver and then i have the remote desktop icon in citrix. i click on the icon and it takes me to a remote ***windows*** desktop. and now starts the issue the Alt + tab dosent work in the remote ***windows*** desktop. whereas it works locally in the ***ubuntu*** system. like if i press alt + tab it shows me all the applicaitons opened in the ***ubuntu*** system along with one remote desktop icon. but i need to toggle between the applications opened within the ***windows*** remote desktop. please help me resolve this issue

note: in ***ubuntu*** when i maximize the window of the remote desktop am able to maximize it, but the taskbar at the top is not disappearing in the remote desktop window. whereas while using it in a ***windows*** system the taskbar disappears when we press Shitf+F12 and then the alt + tab works finely in the remote windows machine.

---

### Post by conbot on 2011-06-18
There might be a way to lock in all keycodes and cursor movement like the Ctrl+Alt option in VMWare Player.

---

### Post by krapp on 2011-06-18
Which Ubuntu are you running?

If you're still on GNOME 2 my guess is that in a conflict between window manager and remote desktop the window manager keybinds take precedence. In other words, the Alt-Tab function works exclusively with Metacity, the window manager. One way to test this is to remap this function to another keybinding in the Keyboard Shortcuts settings, and then see if that frees up Alt-Tab for Windows.

---

