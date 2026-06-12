---
title: "Keyboard shorcut to gnome-system-monitor"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by DMKryl on 2011-01-18
Today i found gnome-system-monitor and i want to configure it to ctrl+alt+del, there was a shotcut there but i moved when i configured the shorcut to open the gsm whis window appeared

Error while trying to run ($ gnome-system-monitor)
which is linked to the key (<Control><Alt>Delete)

---

### Post by wojox on 2011-01-19
You ran these commands in the terminal:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gnome-system-monitor"
```

---

### Post by DMKryl on 2011-01-19
thx for your help but it didn't work, the problem was that i've put "$ gnome-system-monitor" the $ was the mistake, silly mistake.

---

