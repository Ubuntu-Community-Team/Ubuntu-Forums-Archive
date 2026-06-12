---
title: "Whats the correct way to shut down when machine locks?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by richlewt on 2009-07-11
Hi
My installation is a little flakey at the moment and I am getting several frozen sessions.
I windows I do a CTRL-ALT-DEL to give me a task manager which I can choose to shut applications or do a restart.
What is a similar thing to do in Ubuntu?

---

### Post by Cato2 on 2009-07-11
There are a few things you can do:

- use GNOME System Monitor to kill the offending process(es) - sort by CPU to see the processor hogs.  Best to run this all the time.

- Ctrl/Alt/Backspace - this kills your X Windows session (GNOME/KDE etc, and all applications) so it's quite drastic.  You should then be able to log in again.

- Alt/SysRq and R, S, E, I, U, B - this will save any in memory data to disk, kill all processes, unmount all filesystems, and then reboot.  You must hold down both Alt and SysRq while doing all the R, S etc characters.  The acronym is Raising Skinny Elephants Is Utterly Boring ....  Search for 'magic sysrq key' to find out more.

The latter is not much different to turning off the power, but a little safer for your disks.

See [http://ubuntuforums.org/showthread.php?t=47990](http://ubuntuforums.org/showthread.php?t=47990) as well.

---

### Post by CLomax on 2009-07-11
> **Cato2 said:**
> - Ctrl/Alt/Backspace - this kills your X Windows session (GNOME/KDE etc, and all applications) so it's quite drastic.  You should then be able to log in again.
As of 9.04, this ability has been removed.

---

### Post by Bradtek on 2009-07-11
Above suggestions +

If you can open a terminal, type
```
sudo reboot -n
```
to reboot

If you can not open a terminal box try Holding Ctrl Alt F2
which should take you to a non GUI terminal where you will need to login and try above suggestions.

Ctral Alt F7 gets you back to GUI session

---

### Post by braete on 2009-07-11
> **CLomax said:**
> As of 9.04, this ability has been removed.

no it hasnt been removed

it is deactivated (cuz of accidental xkill)

install dontzap via synaptic and run sudo dontzap --disable to reenable

---

### Post by FoxFireX on 2009-07-11
No need.


Navigate up to System Preferences -> Keyboard Shortcuts.

There is already a shortcut enabled for Ctrl + Alt + Del, its named Log Out, look for it, then click on the shortcut keys and hit backspace I think.

Then make a new shortcut, and the command for it will be "gnome-system-monitor" Name it whatever you want, and make the shortcut ctrl alt delete, or something else if you'd like, use the key grabber to make the shortcut it might be easier for you.

Then the newly created shortcut will be at the bottom of that window so scroll down and 
thats where you make the hot keys for it.

---

### Post by Mornedhel on 2009-07-11
> **Cato2 said:**
> - Alt/SysRq and R, S, E, I, U, B - this will save any in memory data to disk, kill all processes, unmount all filesystems, and then reboot.  You must hold down both Alt and SysRq while doing all the R, S etc characters.  The acronym is Raising Skinny Elephants Is Utterly Boring ....  Search for 'magic sysrq key' to find out more.

I would like to add that since this is implemented at the kernel level, it will almost always work, even if X is frozen, and even in the rare case where you can't even access a console.

---

