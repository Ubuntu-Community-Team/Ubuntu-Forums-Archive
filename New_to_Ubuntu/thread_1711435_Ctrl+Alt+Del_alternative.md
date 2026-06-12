---
title: "Ctrl+Alt+Del alternative"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2011-03-21
I am able to crash even Ubuntu.
I tried that...
writing in terminal this:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
and then this:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

... and it didn't work. :confused:

So, how could I attach "gnome-system-monitor" to ctrl+alt+del shortcut key combination?

---

### Post by 5149.5 on 2011-03-21
The ctrl+alt+del shortcut key combination is assigned to the logout process. You can change that using the keyboard shortcut app.

---

### Post by Nikola Georgiev on 2011-03-21
> **5149.5 said:**
> The ctrl+alt+del shortcut key combination is assigned to the logout process. You can change that using the keyboard shortcut app.
From the keyboard shortcuts app I can change to what combination is assigned the log-out process, not to what process is assigned the ctrl+alt+del shortcut key combination.
There is no "open system monitor" option there.

---

### Post by 5149.5 on 2011-03-21
> **Nikola Georgiev said:**
> From the keyboard shortcuts app I can change to what combination is assigned the log-out process, not to what process is assigned the ctrl+alt+del shortcut key combination.
There is no "open system monitor" option there.

Correct, there is no way to do your key assignment if it is already set to something.

---

### Post by Stratosjack on 2011-03-21
yeah, try to open the Terminal instead (ctrl+alt+T for me)... you can use the 'kill' command or 'xkill'

---

### Post by Nikola Georgiev on 2011-03-21
> **5149.5 said:**
> Correct, there is no way to do your key assignment if it is already set to something.
The combination is not set to anything right now... :?

> **Stratosjack said:**
> yeah, try to open the Terminal instead  (ctrl+alt+T for me)... you can use the 'kill' command or 'xkill'
Yes, I have a shortcut key combination for Termninal too. But:
Does the Terminal open even if the whole system is crashed? (like the ctrl+alt+del in windows)?
Also, how could I know what is the exact name of every process?

---

### Post by Stratosjack on 2011-03-21
the task manager in windows is just another process... it could crash too
i've never been unable to open the terminal in ubuntu..
the only thing is when some application crashes, like a movie player or something, which i usually terminate with *xkill*... 
in any case, you can always open a terminal and type in *gnome-system-monitor*, find the process you need and then just kill it...
hope it helps

---

### Post by Stratosjack on 2011-03-21
yeeeah, I did it...
check this out: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)
this should work...

---

