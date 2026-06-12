---
title: "ctrl alt delete for ubuntu"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by thomz92 on 2009-12-04
is there a command similar to the ctrl alt delete command for ubuntu? I want it to work no matter what programs are open and no matter whats happening. i need it to be able to kill a non-responding program. thanks in advance

---

### Post by Paqman on 2009-12-04
Alt-F2, type:```
xkill
```and click on the offending app. You can also kill or end processes through the System Monitor.

---

### Post by JamesParnell on 2009-12-04
right click on one of yours panels, select add to panel.
 
 
then search for "force quit" (i think thats the name)
 
then simply click the icon hover over the naughty program and click, the app will then force the program to quit
 
Paqman beat me to it :P

---

### Post by thomz92 on 2009-12-04
thanks for the fast reply. ok i guess i should have been more specific...what if the program is running full screen (no panels showing or anything)? does it still work?

---

### Post by Jim_in_Germany on 2009-12-04
The thing you are looking for which is most like Task Manager in Windows is called System Monitor.
Here you will find a list of all processes running and be able to kill an non-responding one.
Normally you would find it under Administration -> System Monitor.
In Ubuntu the ctrl+alt+del combo is used when powering down the computer.
You can however change this, so that this combo calls up System Monitor (in case of a near total lock-up).

Here's how:

Open System - Preferences - Keyboard short cuts
Click add
Name: System Monitor
Command: usr/bin/gnome-system-monitor
Click apply.

Now if you scroll down you will see your short cut listed under 'Custom short cuts'
Click where it says 'Disabled' and it will prompt you to enter a new short cut. Now hold down ctrl, alt and delete. Don't type anything, just press the buttons on your keyboard.
It will warn you that ctrl+alt+delete is set to help shut down the computer and that if you proceed you will override this.
Override it anyway and you will have the short cut.

---

### Post by thomz92 on 2009-12-04
ok great! but does this work even when a program locks up?

i've tried ctrl-alt-delete before becuase i new it was supposed to show the different options for shutting down the computer, or hibernating, etc. and i thought that if it popped up, so would the panels and then maybe i could get to system monitor from there, but nothing happened. so i was wondering if i changed ctrl-alt-delete to open the system monitor, if it would actually do something.

i think paqman's idea might work, but if it doesn't work when a fullscreen program is locked up, than its not what im looking for.

---

### Post by 0xABC123 on 2009-12-04
Such a key combo used to exist but Ubuntu devs removed it :cry: (ctrl+alt+backspace)

---

### Post by zkriesse on 2009-12-04
> **thomz92 said:**
> thanks for the fast reply. ok i guess i should have been more specific...what if the program is running full screen (no panels showing or anything)? does it still work?
Yes it will my friend...I use that for bad and naughty programs.

---

### Post by thomz92 on 2009-12-04
so my only option is

> Alt-F2, type:
Code:

xkill

and click on the offending app. You can also kill or end processes through the System Monitor.

---

### Post by ssulaco on 2009-12-04
> **thomz92 said:**
>  I want it to work no matter what programs are open and no matter whats happening.
Alt+PrintScreen+r+s+e+i+u+b 
hold the alt/printscreen together while you cycle threw rseuib
while cycling threw the letters hold each one up to 5sec
This works for me if I have a total Freeze

A way to remember rseiub:
Raising Skinny Elephants Is Utterly Boring

---

### Post by samh785 on 2009-12-04
> **0xABC123 said:**
> Such a key combo used to exist but Ubuntu devs removed it :cry: (ctrl+alt+backspace)
[http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html)

---

### Post by Simian Man on 2009-12-04
Try:
[LIST=1]
[*]Ctrl-Alt-F2
[*]Login
[*]killall -9 <name of program>
[/LIST]

Not user-friendly, but always works.

---

### Post by Paqman on 2009-12-04
> **thomz92 said:**
> 
i think paqman's idea might work, but if it doesn't work when a fullscreen program is locked up, than its not what im looking for.

It will, yes. The Alt-F2 launcher will always be on top of all the other windows.

---

### Post by fromthehill on 2009-12-04
> **ssulaco said:**
> Alt+PrintScreen+r+s+e+i+u+b 
hold the alt/printscreen together while you cycle threw rseuib
while cycling threw the letters hold each one up to 5sec
This works for me if I have a total Freeze

wouldn't holding the printscreen button result in a lot of screenshot dialogs? :p

---

### Post by mgmiller on 2009-12-04
For Karmic, in keyboard preferences on the layouts tab / layout options, there is a spot where you can reenable ctrl alt backspace as the keys to restart the x-server.

Also, you can use alt/prtscrn/k to do the same thing.  Some times you don't need to do a whole restart, which alt/prtsrcn/rseiub will do.  Just doing the "k" will restart x without rebooting.

---

### Post by lotharmat on 2009-12-04
I've never got that to work - Do you have to enable it in the Kernel or something?

---

### Post by thomz92 on 2009-12-04
ok i think i got what i wanted from samh785. i followed the instructions from your link and it worked perfectly. now comes the final test...when a program actually crashes :) i don't doubt that it'll work tho. thanks everyone for the help!!

---

### Post by 3rdalbum on 2009-12-04
> **0xABC123 said:**
> Such a key combo used to exist but Ubuntu devs removed it :cry: (ctrl+alt+backspace)

1. No, the Xorg developers disabled that particular combination by default...

2. ...and instead implemented the same function at Alt-Printscreen-K (Alt-SysRq-K).

This kills the X server, which instantly kills all running graphical programs. This is only really for use when the whole X locks up, which doesn't seem to happen much these days (at least for me).

If you have one fullscreen program that you want to kill, switch to another VT (press Control-Alt-F1) and kill the program on the command-line, or use the 'top' program to find it and kill it. Then switch back to X by pressing Control-Alt-F7.

---

### Post by bruno9779 on 2009-12-04
I always use:

```
Ctrl+Alt+F1
```

to open a TTY session.

There you just have to log in and:

```
sudo killall *nameofprocess*
```

(often I have to do it twice to be effective)

then:
```
Ctrl+Alt+F7
```

to go back to desktop.

On my opinion this is by far the best way to kill an unresponsive app on fullscreen

---

### Post by Paqman on 2009-12-04
> **thomz92 said:**
> now comes the final test...when a program actually crashes :) 

You don't need to wait. Trying it out by killing a regular desktop app like your browser won't do anything nasty to your system.

---

### Post by Excedio on 2009-12-04
Applications > System Tools > Configuration Editor
 
Once in the program:
apps > metacity > global_keybindings
 
run_command_# (Pick a number)
```
gmone-system-monitor
```
 
 
Now go to:
apps > metacity > keybinding_commands
 
Find the command number that corresponds to the one you used before
```
<Control><Alt>Page_Down
```
 
 
Now that if you've done this, whe you press Ctrl+Alt+PageDown at the same time, it will bring up the gnome system monitor and you can kill any process.
 
Hope that helped. :-)

---

### Post by thomz92 on 2009-12-04
> It will, yes. The Alt-F2 launcher will always be on top of all the other windows.

i tried it in the "world of goo" demo and it didn't work...which makes me wonder if this really does work with fullscreen programs. I dont know if its a computer specific problem...trying to switch workspaces with ctrl-alt-right arrow key doesn't work either when in a full screen program, but otherwise it works...

---

### Post by thomz92 on 2009-12-04
> If you have one fullscreen program that you want to kill, switch to another VT (press Control-Alt-F1) and kill the program on the command-line, or use the 'top' program to find it and kill it. Then switch back to X by pressing Control-Alt-F7.

i'd like a GUI if at all possible...im much more comfortable that way

---

### Post by hobo14 on 2009-12-04
**Right Alt + Print Screen + K**

will dump you out to the login screen (GUI, not command line), no matter what.  Replacement for Ubuntu's old Ctrl-Alt-Bkspc.

---

### Post by thomz92 on 2009-12-04
> Right Alt + Print Screen + K

will dump you out to the login screen (GUI, not command line), no matter what. Replacement for Ubuntu's old Ctrl-Alt-Bkspc.

IMHO, thats not much better than pushing the power button and restarting the whole computer. Does anyone know of a foolproof way to get system monitor running no matter what program, fullscreen or otherwise, is open?

---

### Post by sandyd on 2009-12-04
i simply mapped ctrl+alt+del to xkill.
works wonders
in fullscreen apps, just click anywhere and the app will close.
nvm. for some reason, works for some apps but not others.

---

### Post by lotharmat on 2009-12-05
I still cannot get atl+SysRq+k to work.

Boo!

---

