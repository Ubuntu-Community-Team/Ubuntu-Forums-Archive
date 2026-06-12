---
title: "Taskmanager in linux?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-21
Hi everyone,

Is there something like the windows taskmanager in linux.


In recent times my system froze or I couldn't get out of a application
(I always resolved this issue by simply turning off the computer which isnt really good)


Anyone have any suggestions??

---

### Post by PukingPenguin on 2009-03-21
You can try the following:
Alt+SysRq+REISUB

---

### Post by LowSky on 2009-03-21
there is an applet called force quit, just add it to your top or bototm panel, its very helpful otherwise, there is Ctrl+Alt+Backspace  which does a mini reboot to the login screen.

NOTE the next version 9.04 Disables Ctrl+Alt+Backspace (don't know why but annoying to a longtime user)

---

### Post by OutOfReach on 2009-03-21
Go to System>Administration>System Monitor
then to the Processes tab

---

### Post by SunnyRabbiera on 2009-03-21
Indeed, the system monitor is our answer to the windows task manager.

---

### Post by balaknair on 2009-03-21
System Monitor
System menu> Administration> System Monitor

Or, press Alt+F2--> gnome-system-monitor

If everything in the GUI freezes up and you can't launch even the system monitor, instead of hard-resetting the computer, try *Ctrl-Alt-Backspace*. This causes just the GUI(called X-Windows) to restart, without harming the underlying system.

---

### Post by ibutho on 2009-03-21
If you use GNOME, then gone-system-monitor is a good tool to manage processes and resources for your system. For those using KDE, ksysguard does the same thing. Other commands that maybe useful are top and htop. To kill frozen gui apps, you can use xkill.

---

### Post by binbash on 2009-03-21
you can give ps aux command and kill the pid number with kill number command or you can do something like pkill firefox

---

