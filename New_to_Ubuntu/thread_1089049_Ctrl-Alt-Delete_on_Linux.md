---
title: "Ctrl-Alt-Delete on Linux?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by italianoman421 on 2009-03-06
I'm using ubuntu linux, and just had my internet screen freeze. I tried the old windows standby of Ctrl-Alt-Delete and nothing happened, what is the equivalent of that on ubuntu linux.

---

### Post by Vonnick on 2009-03-06
The task manager equivalent is System>Administration>System Monitor.

I don't know if there is a key combo, sorry.

---

### Post by kanikilu on 2009-03-06
If it's just firefox that has locked up, press ALT+F2, in the dialog box that comes up, type **xkill** and press enter. xkill will kill the process of whatever window you click on next.

You can also go to the terminal (Applications > Accessories > Terminal) and then type ```
ps -ef | grep firefox
``` The output should look something like this > username 24822     1  3 08:38 ?        00:17:43 /usr/lib/firefox-3.0.7/firefox The process number (PID) is the number after your username. You can then issue the following to kill it ```
kill -9 24822
``` (substitute in your own PID, of course).

---

### Post by mgmiller on 2009-03-06
If it's just the browser that froze and you can still use other parts of system, click on Applications > Accessories > Terminal

In the window that opens type:
```
xkill
```

The cursor will change to a skull and crossbones.  Just put that over the frozen program and left click.  It will shut down the application almost instantly.

You could also try going to System > Administration > System Monitor and clicking on the Processes tab and then scrolling down till you find Firefox and then right clicking it and selecting "Kill process".  But the terminal command is much more fun.

If the whole desktop seems frozen, you can usually do ctrl-alt-backspace  which will restart the gui and bring you back to the log in screen without having to reboot the whole computer.

There are other ways around this problem also, but these should get you through 98% of any problems you encounter.

---

### Post by linuxisevolution on 2009-03-06
Just type sudo killall firefox in a terminal or hit ctrl+alt+backspace .

---

### Post by kanikilu on 2009-03-06
I sometimes forget that there are more user-friendly ways of doing some things ;)

You can, of course, use gnome-system-monitor to find and kill the offending process in a GUI, but it never hurts to know how to do things from the command line.

---

### Post by kanikilu on 2009-03-06
> **linuxisevolution said:**
> Just type sudo killall firefox in a terminal or hit ctrl+alt+backspace . True, but it's probably worth just noting, though, that CTRL+ALT+BKSP will end your entire session and take you back out to the login, which is fine if you know it's coming. Otherwise, if you know what process is causing a problem, and it's just that one, just kill it rather than restarting X or worse rebooting.

// Edit - I'm sure most people are aware of this, but just for the sake of the OP...

---

### Post by Jubward on 2009-03-06
Well if your computer completely locks up you could always do Ctrl+Alt+F2, but you shouldn't do that unless you need to. But if it's just your browser and if for some reason you can't click the system tab you can use Alt+F2 to access a terminal and kill firefox.

---

