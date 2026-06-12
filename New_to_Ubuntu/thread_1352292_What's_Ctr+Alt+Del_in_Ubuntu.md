---
title: "What's Ctr+Alt+Del in Ubuntu?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by bwzz on 2009-12-11
My question is: what to do when a program in Full Screen mode hangs?
Tried several combinations but still couldn't figure it out....

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
Hit Alt+f2 then run xkill.
click on the unresponsive window

---

### Post by doas777 on 2009-12-11
well CAD does work, but it brings up the shutdown menu.
you can use Alt + F4 to kill the focus window, 
or you can use alt-F2 to show the run bar, and invoke gnome-system-monitor, or to open a terminal and use killall from there.

---

### Post by philinux on 2009-12-11
And if it really really gets hung.

Alt+SysRq+k

This will kill x and log you out.

---

### Post by beetleman64 on 2009-12-11
Alt + F2 will bring up xkill, then click on the offending application.

By the way, Ctrl + Alt + Del used to restart the X Server, but it doesn't anymore

---

### Post by cartisdm on 2009-12-11
> **beetleman64 said:**
> Alt + F2 will bring up xkill, then click on the offending application.

By the way, Ctrl + Alt + Del used to restart the X Server, but it doesn't anymore

I thought it was Ctrl + Alt + Backspace?

---

### Post by lessmemorelove on 2009-12-11
"control alt delete" can actually be set to do whatever you want it to. just check out your keyboard settings under prefs. as for an unresponsive window, use xkill like others have said or gnome system monitor or turn your "control alt backspace" combination on to restart x. ;)

---

### Post by Psumi on 2009-12-11
> **cartisdm said:**
> I thought it was Ctrl + Alt + Backspace?

You need to disable dontzap for CRTL+ALT+Backspace to restart x.

And yes, it is.

---

### Post by oldsoundguy on 2009-12-11
If you are running Gnome, you can put a force quit applet in your panel.  It is already there in the list of adds. Beats the keystrokes.

---

### Post by bwzz on 2009-12-11
ALT+F2 just didn't show up anything...
ALT+F4 didn't close the program either.
Alt+SysRq+k effect is overwhelming, though it works, but kills everything, while I only need to kill the current hanging program.

---

### Post by philinux on 2009-12-11
> **bwzz said:**
> ALT+F2 just didn't show up anything...
ALT+F4 didn't close the program either.
Alt+SysRq+k effect is overwhelming, though it works, but kills everything, while I only need to kill the current hanging program.

I meant really really hung, as in nothing else works.;)

---

### Post by doas777 on 2009-12-11
it's worrisome that your gnome keybindings are not operating correctly. I wonder what it is that is hung?

---

### Post by bwzz on 2009-12-11
> **doas777 said:**
> it's worrisome that your gnome keybindings are not operating correctly. I wonder what it is that is hung?
It's a 3D car rally game called "Trigger"

---

### Post by doas777 on 2009-12-11
> **bwzz said:**
> It's a 3D car rally game called "Trigger"

see, I wonder if trigger is the cause, or if it just hangs because underneath gnome is behaving badly. it is also quite possible that the game is overriding certian gnome operations (full screen games do that a lot).

will the key commands work correctly when you are not playing the game? 
also do you use compiz? it overrides some gnome key and mouse bindings. 

can you use Crtrl + Alt + F1 to bring up a vTTY? if so, next time it freezes I would be interested what the top process is in 'top', and the contents of 'sudo dmesg | tail'

---

### Post by bacardiandwatermelon on 2009-12-11
I'm used to the old habits, I enable the ctrl+alt+backspace (restart x server) by going to System->Preferences->keyboard->layout->layout options->key sequence to kill x server... tick

---

### Post by pbrane on 2009-12-11
In a graphical environment like GNOME or KDE you usually need to do a **CTRL+**ALT+F2 to get the second VT. ALT+F2 will bring up the run menu. When you get to a vTTY you can login and kill the offending program. sometimes you have to find the PID and sudo kill -9 *offending PID*

---

### Post by doas777 on 2009-12-11
> **pbrane said:**
> In a graphical environment like GNOME or KDE you usually need to do a **CTRL+**ALT+F2 to get the second VT. ALT+F2 will bring up the run menu. When you get to a vTTY you can login and kill the offending program. sometimes you have to find the PID and sudo kill -9 *offending PID*

I usually find 
killall <processname> 
more intuitive.

---

### Post by durand on 2009-12-11
> **bacardiandwatermelon said:**
> I'm used to the old habits, I enable the ctrl+alt+backspace (restart x server) by going to System->Preferences->keyboard->layout->layout options->key sequence to kill x server... tick

Wow, didn't know you could do that!

---

### Post by jrandolph on 2009-12-11
> **durand said:**
> Wow, didn't know you could do that!

I didnt either - I have kinda missed the command 
now i have it back
Thanks

---

### Post by inspiteofmyself on 2009-12-11
good lord some of the replies in here. lol...

alt-f2 will open the run dialog. more than likely your problem has to do with graphics drivers. CTRL-ALT-BACKSPACE used to restart X and gdm but does not do so by default anymore... i would not do it.

you can do something like CTRL-ALT-[F1-F6] to change to a text console to work on the command line to kill the game. odds are you ran an exectuable called 'trigger'. if you do not know how to work with process id's, try doing 'killall -KILL trigger'.

i have had some problems with some games and the nvidia drivers that are installed through restricted drivers. some of them just seem to freeze everything up. changing to another desktop and back usually fixes it and frees up the driver though. to do that, do CTRL-ALT-RIGHT_ARROW and then CTRL-ALT-LEFT_ARROW. in particuliar i have problems with tabbing away from some games making everything (including the mouse cursor and the ALT-F2 run dialog) appear to be frozen.

if all else fails and you really are stuck...resort to Alt+SysRq+k

---

### Post by ECPCLINUX on 2009-12-11
Try this:

System-Preferences-Keyboard Shortcuts

Then click on the ADD button. A small window will pop up, For the Name: you may use whatever you want, I personally use Task Manager. For the Command: Copy & Paste the following below:

gnome-system-monitor

This new command will be at the end of the list, right click it and use the keys control+alt+del. it will open a small windows telling you that this command is already in use. just accept to change it to the new command contol+alt+del. That's it, it should work, it worked for me on Ubuntu 9.10 x64.

---

