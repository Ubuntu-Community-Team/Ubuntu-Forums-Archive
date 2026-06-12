---
title: "Key Values"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-09-08
I am new to Linux and Ubuntu and I have been trying to create keyboard shortcut commands with the usual method with keybindings and I have a question about key values. Where/how do I find them? Is it the path that I need, or what? Please point me to any information that would help. Thank you.

---

### Post by CJWW1989 on 2009-09-08
Can anyone please help me with this? I read something about finding the path through the which command on the shell, but obviously I have no idea what this is. If anyone knows, please post. Thank you.

---

### Post by Mornedhel on 2009-09-08
You can get a keycode value (the value sent to the X server when a key is pressed) by running xev, and pressing a key while looking at the terminal. The keycode will be displayed (along with a lot more information).

The which command is used to return the full path to another command, for instance "which ls" returns "/bin/ls". You may need this if you want to create a shortcut, but usually just "ls" works.

---

### Post by CJWW1989 on 2009-09-08
> **Mornedhel said:**
> You can get a keycode value (the value sent to the X server when a key is pressed) by running xev, and pressing a key while looking at the terminal. The keycode will be displayed (along with a lot more information).

The which command is used to return the full path to another command, for instance "which ls" returns "/bin/ls". You may need this if you want to create a shortcut, but usually just "ls" works.

Thank you for your help but I'm either not understanding this or didn't explain myself correctly. I am trying to make a shortcut, and I am asking how do I find the value to input in apps/metacity/keybinding_commands to make things open. Like I am trying to have my system monitor open with <control><alt>s. I read somewhere to use gnome-system-monitor as the value, but that doesn't work. Does this change the directions any? Thank you.

---

### Post by Mornedhel on 2009-09-08
OK, I think I get what you meant. My confusion came from the fact that you've been using key/value in the gconf sense, and I thought you meant key as in keyboard and value as in keycode value.

According to the documentation string displayed when you select one of the command_* keys in apps/metacity/keybinding_commands, you need to enter a command there. Just "gnome-system-monitor" should be good ; if not, execute "which gnome-system-monitor" in a terminal and use the result.

Then you need to go to apps/metacity/global_keybindings and enter the appropriate value for the command_* key you used in the previous step.

Unfortunately, those are Metacity keybindings, and I can't help you much further, because I've switched from Metacity to another window manager some time ago. This also means **I can't test the method I just described**. If it works, good ; if it doesn't, I can't tell you why and I probably can't help.

Incidentally, my reason for switching to the Sawfish window manager was to be able to associate any keybinding to any action or command. The switching process is rather involved, though, and probably not a good idea for a full beginner.

---

### Post by Excedio on 2009-09-08
Here is how I set mine...
 
global_keybindings.....run_command _4.....<Control><Alt><Page_Down
keybinding_commands.....command_4.....gnome-system-monitor
 
Make sure you match up the run_command_# with command_#

---

