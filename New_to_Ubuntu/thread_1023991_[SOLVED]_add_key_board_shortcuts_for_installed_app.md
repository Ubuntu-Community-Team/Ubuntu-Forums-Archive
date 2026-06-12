---
title: "[SOLVED] add key board shortcuts for installed applications"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by bob brazie on 2008-12-28
How can I add key board shortcuts for installed applications in 8.10 that are not listed in the keyboard shortcut menu?

Applications such as the text editor gedit?

Thanks in advance. Bob.

---

### Post by ibuclaw on 2008-12-28
Press **Alt+F2** and type in:
```
gconf-editor
``` in the run command box.
Now dive into the following folder in the mini registry editor:
```
/apps/metacity/keybinding_commands
```
And give as many commands as you wish an executable tag.
ie:
```

**Name:           Value:**
command_1       gedit
```
Once finished, go into the **global_keybindings** folder path and give each command a key binding:
ie:
```

**Name:           Value:**
run_command_1   <Super>G
```
The "Super" key will be your Left WinKey.

And you are all set! Though be careful not to have a generic keybinding, else you may find that it clashes with another application.

Regards
Iain

---

### Post by Elfy on 2008-12-28
Open gconf-editor with the Alt+F2 run dialog.

Navigate to /apps/metacity 
as an example I run xchat form the Calc button 

global_keybindings > run_command_1 - set the key combination here
keybinding_commands > command_1 - set the command to run

So I have the keybinding set to XF86Calculator and the command to /usr/bin/xchat

---

### Post by bob brazie on 2008-12-28
OK I set:keybinding_commands

Name:           Value:
command_1       gedit

Then:global_keybindings

Name:           Value:
run_command_1   <Ctrl><Alt>n

When I close and try the combination nothing happens.

any suggestions? <g>

---

### Post by ibuclaw on 2008-12-28
> **bob brazie said:**
> OK I set:keybinding_commands

Name:           Value:
command_1       gedit

Then:global_keybindings

Name:           Value:
run_command_1   <Ctrl><Alt>n

When I close and try the combination nothing happens.

any suggestions? <g>

Use proper english to describe the keys, not abbreviations. :)

```
<Control><Alt>n
```

Regards
Iain

---

### Post by bob brazie on 2008-12-28
Strange here is the explination given in the keybindings area:

The keybinding that runs the correspondingly-numbered command in /apps/metacity/keybinding_commands The format looks like "<Control>a" or "<Shift><Alt>F1". The parser is fairly liberal and allows lower or upper case, and also abbreviations such as "<Ctl>" and "<Ctrl>". If you set the option to the special string "disabled", then there will be no keybinding for this action.

---

