---
title: "Gnome, How to map Ctrl+C as F5 and Ctrl+V as F6"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by tenkamuteki82 on 2011-07-14
Hi,

is it possible to map Ctrl+C as F5 and Ctrl+V as F6 in gnome environments? How do we do it?

---

### Post by relay_man on 2011-07-16
I've not done it, but this suggests you can.

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

Hope this helps

---

### Post by tenkamuteki82 on 2011-09-21
I tried that, but no luck in terms of the F1-12 keys


Does anyone know how to map the F5 on the keyboard to do ctrl + c?

---

### Post by tenkamuteki82 on 2011-09-25
So it seems like gnome might do it, but Copy and Pasting still does not work through the gui.

Can anyone provide guidance on how to map CTRL C and CTRL V? Thank you so much

---

### Post by Krytarik on 2011-09-25
Based on your thread, I've just established this way to achieve your target:

1. Create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:
```
keycode 71 = XF86Copy XF86_Switch_VT_5 XF86Copy XF86_Switch_VT_5
keycode 72 = XF86Paste XF86_Switch_VT_6 XF86Paste XF86_Switch_VT_6
```The next time you log in, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

*depends on if you had such a file before, and did already confirm/disable those query


2. Install the package "lineakd":
```
sudo apt-get install lineakd
```3. In "Keyboard Shortcuts", under "System -> Preferences" in classic Gnome, add two shortcuts for these commands:
```
sh -c "xsendkeycode 71 0; xsendkeys Control+c"
``````
sh -c "xsendkeycode 72 0; xsendkeys Control+v"
```4. In "gconf-editor", run via Alt+F2 or terminal, find the newly added shortcuts under paths like this (where "X" is a number, counting up from 0):

"/desktop/gnome/keybindings/customX"

And set the value for "binding" to "XF86Copy", respectively "XF86Paste".

Have fun! :D

---

### Post by tenkamuteki82 on 2011-10-05
Thank you so much! This is wroking!! wow... i wonder if it is working for both gnome2 and gnome3...

can you tell me how to modify it so that I use F7 and F7 keys instead? i realized F5 is for my browser refresh so its not good

Thanks sooooooooo much

---

### Post by Krytarik on 2011-10-05
Finally! :P I've already started wondering if I've figured all this only for me - meaning for fun, because I don't use those method, at least not so far. :D

> **tenkamuteki82 said:**
> i wonder if it is working for both gnome2 and gnome3...Yep, I guess so, as this isn't really a Gnome thing - at least not per-se, some menus/dialogs might be different, though - , but only depends on X; and if you're referring to Oneiric 11.10, it's still based on X.

> **tenkamuteki82 said:**
> can you tell me how to modify it so that I use **F7 and F7** keys instead? i realized F5 is for my browser refresh so its not good
Are you meaning F7 and F8 instead? :P

In any case, here are the additional keysym lines - the default ones, for clarity - , I guess you'll get the point how to adapt the instructions to them :D :
```
keycode  73 = F7 XF86_Switch_VT_7 F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8 F8 XF86_Switch_VT_8
```

---

