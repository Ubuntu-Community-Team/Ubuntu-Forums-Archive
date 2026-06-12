---
title: "Set Ctrl+Alt+Del to open gnome-system-monitor"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by jimingkui on 2009-09-26
I try to add Ctrl+Alt+Del to open up gnome-system-monitor from *System->Administration->Keyboard Shortcuts*.
But it doesn't work,anyone help?I'm using ubuntu 9.04

---

### Post by Sir Jasper on 2009-09-26
Hi,

Alternatively, you install Gnome-Do, then Winkey+Spacebar, type sy and return.

If you do that a few times just typing s will work.

My regards

---

### Post by CaptainMark on 2009-09-26
urgh windows. Just let it go. Bill cant hurt you anymore.

---

### Post by theozzlives on 2009-09-26
Originally ctrl+alt+del was to restart your system (3 finger salute), NOT to bring up task manager! Linux is NOT Windows. There is no task manager, task bar, or start button. Linux and Unix proved you could have a 32 bit & 64 bit command prompt. Microsoft forced everyone into Windows claiming they couldn't do that with DOS... lies, all lies. Oh, how I long for the black and white prompt with commands I know!

---

### Post by Jim_in_Germany on 2009-09-26
So, now a helpful reply :)
Do the following:
Open System - Preferences - Keyboard short cuts
Click add
Name: System Monitor
Command: usr/bin/gnome-system-monitor
Click apply.

Now if you scroll down you will see your short cut listed under 'Custom short cuts'
Click where it says 'Disabled' and it will prompt you to enter a new short cut. Now hold down ctrl, alt and delete. Don't type anything, just press the buttons on your keyboard.
It will warn you that ctrl+alt+delete is set to help shut down the computer and that if you proceed you will override this.
Override it anyway and you will have your short cut.

---

### Post by ceramicm on 2009-09-26
Hmm... I too find Ctrl-Alt-Del to be a useful shortcut for the Task Manager.

Here is how to enable it:
1. Open a terminal (Applications, Accessories, Terminal)
2. Copy and paste each of the following lines into the terminal:
```
	gconftool-2 -s --type string /apps/metacity/global_keybindings/run_command_10 "<Control><Alt>Delete"
	gconftool-2 -s --type string /apps/metacity/keybinding_commands/command_10 "gnome-system-monitor"
	gconftool-2 -s --type string /apps/gnome_settings_daemon/keybindings/power ""
```

These lines set up a new keybinding (keyboard shortcut) to gnome-system-monitor, and disable an old binding to the shutdown dialog.

Hope this works for you!

Edit: Aargh! Jim beat me to it! Sorry about that!

---

