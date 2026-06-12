---
title: "System Monitor Hotkey"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by AxelMan0 on 2009-08-02
I would like to make a hotkey for the system monitor but it's not in System > Preferences > Keyboard Shortcuts. How can I go about doing this?

---

### Post by swoll1980 on 2009-08-02
> **AxelMan0 said:**
> I would like to make a hotkey for the system monitor but it's not in System > Preferences > Keyboard Shortcuts. How can I go about doing this?
```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
```
Then:
```
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

That will set it for ctrl+alt+del

---

### Post by AxelMan0 on 2009-08-02
Thanks :)  I'd like to make it ctrl+alt+` though since it's near the escape key and ctrl+alt+del is already mapped to logout. Can I just replace "Delete" with the backtick or is there a special name for backtick that I need to use in the terminal?

---

### Post by AxelMan0 on 2009-08-02
I bound it to ctrl alt insert for now, but I'd still prefer the backtick--I'd hate to accidentally activate the insert thing and start typing over text.

---

