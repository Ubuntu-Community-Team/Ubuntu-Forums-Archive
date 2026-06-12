---
title: "keyboard mapping - remap ALL function keys"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-19
I'm using 64 bit Ubuntu 10.4

I have a Logitech Illuminated Keyboard which, under Windows, using Logitech's SetPoint software, I was able to set (for example) my F1-F7 keys to:

Ctrl-u (underline)
Ctrl-i
Ctrl-b
Ctrl-c
Ctrl-v
Ctrl-x
shift-delete

Under Ubuntu/Gnome I tried two different approaches:

**First:**

System > Preferences > Keyboard Shortcuts

* create a script - in this case containing
xsendkeycode 37 1;xsendkeycode 30 1;xsendkeycode 30 0;xsendkeycode 37 0

(get the keycodes for x using xmodmap -pke, do xmodmap -pke > filename)
(37 is Left Control, 30 is the letter u, (105 is Right Control))

(The values for X and the values for the Kernel are entirely different.)

Give the script full execute permissions

Click ADD
Name your custom shortcut
key the full path and filename of your script in the Command box

I made mine SendCtrlU

Click on Disabled, and press the F1 key

F1 will now run the script (supposedly)

**Second:**

Do the following (install the gconf-editor if it hasn't been)

sudo gconf-editor
Select Apps
Select Metacity
Select keybinding_commands

In this case, I set command_1 to Ctrl-U

Select global_keybindings

Change run_command_1 to F1

F1 now issues Ctrl-U

***

Unfortunately, neither of these seems to WORK for me.

There is SOMETHING else missing somewhere. Dunno what.

---

