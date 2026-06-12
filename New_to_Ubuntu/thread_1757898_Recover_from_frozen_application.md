---
title: "Recover from frozen application?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by RotorRick on 2011-05-14
So a few times lately I've come across a program suddenly going grey, and the cursor stops responding well, it doesnt respond to requests to shut down. So my question is, how can I shut down the offending program quickly? And how do I see what is causing the problem in the first place?

---

### Post by robsoles on 2011-05-14
Which GUI/Desktop are you using? 

[http://ubuntuforums.org/showpost.php?p=5127004&postcount=12](http://ubuntuforums.org/showpost.php?p=5127004&postcount=12) to use terminal (it has a typo, last line 'sude' should be 'sudo' - ask more if you don't get it).

In 10.04 using gnome: "System"->"Administration"->"System Monitor" see the 'Processes' tab.

The offending program might be number crunching or even filing frenetically, the window manager 'polls' it and it doesn't respond because it is too busy so the window manager indicates loss of contact with the running process by greying out the window displaying it's output. The absolute majority of times I've pushed things till they greyed out they have recovered though the odd one just needs to be terminated.


To find out if the program has been logging errors to any of the system's logs you could search for the first few letters of the application's name in /var/log/* or (hopefully) more conveniently using "System"->"Administration"->"Log File Viewer" - log entries are usually time-stamped so noting when "something you didn't like" happens is useful if there are entries relating to the app in question.


Any good?  :)

---

### Post by doas777 on 2011-05-14
if you can, before the mouse freezes, try using Alt + F4 to kill it.

if that doesn't do it, try to get to a virtual TTY with Ctrl + Alt + F1. if you can, login, and use a command like:
```
sudo killall <processname>
```

if all else fails, and you just want to safely reboot your system, try this:
Hold down Alt + PrntScrn/SysReq and slowly type the following letters:
```
r e i s u b
```with each letter press, watch the IO light on your PC. if it lights up after a keypress, wait until it goes dark before you press the next key.

if you get no response from reisub, then your kernel is completely locked, and nothing but a hard power cycle will get it going again. on the subsequent boot, watch for boot messages about disk scanning, and if it happens often, you might want to boot to a live CD and run fsck on your partitions every once in a while, and keep an eye on your disks SMART data with Disk Utility. 

these are just good peices of advice to keep in mind for all hard lockups. when looking into the problem, be extra suspicious of drivers. they (or damaged system files) are likely the cause.

---

### Post by mcduck on 2011-05-14
You can also try using SysRq + k to kill the current virtual console (which when done at the desktop will kill the desktop environment and all applications and drop you back to login screen.). A bit smoother approach than a full reboot.

Of course it would be better to just kill the frozen application, if possible. For that, try Alt+F4, System Monitor, top (or htop) and of course xkill. 

Afterwards you can check ~/.Xsessionerrors in case there's something that might explain why the program crashed. And of course starting an app from a terminal would give you a change to catch the errors, so that's worth a try if you are regularly having problems with a certain program.

---

### Post by Paqman on 2011-05-14
Hit Alt-F2, type:
```
xkill
```
and click on the offending window. Easy as that.

Clicking on the normal x button for closing the window a couple of times should also bring up a message asking if you want to "force close" it, which is another option.

---

### Post by jtarin on 2011-05-14
This is when its also  good to have a dropdown terminal accessed by hotkey.....then follow Paqmans advice and type the command "xkill"

---

