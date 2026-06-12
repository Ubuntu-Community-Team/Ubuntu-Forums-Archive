---
title: "Function Keys"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by greymaus on 2009-07-31
Is it possible to program the function keys (F1-F12) and if so, how is that done?

---

### Post by SunnyRabbiera on 2009-07-31
Yeh it can be done, but I suggest using a modifier key along with it.
Like the super key (the key with the windows logo on it)
So you can assign control+super+function key
There is a tool to assign your function keys for this in system> preferancs> keyboard shortcuts.

---

### Post by afeasfaerw23231233 on 2009-07-31
As mentioned above you can assign your function keys for this in system> preferancs> keyboard shortcuts. But there is another way to do so. 

Hit alt+f2 and run gconf-editor. 
In apps > metacity > global_keybindings you can change the value to any key including F1-F12. There are already some present functions. But you can also add your own command. By default run_command_1 to 12 are disabled so you can make use of them to set your own. 

For example, I set <Super>+z as running the command **xset dpms force off** (switching off the backlight). In global_keybindings I changed the value of run_command_1 to <Super>z and in keybinding_commands I changed the value of command_1 to xset dpms force off. It takes effect at once. You don't need to reboot the computer.

Sorry for my English. You can have a look at my screenshots.

[ATTACH]123087[/ATTACH]
[ATTACH]123088[/ATTACH]
[ATTACH]123089[/ATTACH]

---

