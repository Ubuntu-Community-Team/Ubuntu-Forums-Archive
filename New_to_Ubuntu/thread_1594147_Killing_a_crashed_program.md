---
title: "Killing a crashed program"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-12
Is there a shortcut to killing a program that has frozen? I tried to run Computer Janitor and it seems to have frozen at the beginning of the cleaning process, how would I go about killing it and restarting it? In Windows you can ctrl+alt+del, so does Ubuntu have a similar function?

Thank you

---

### Post by yetiman64 on 2010-10-12
There are several commands in terminal such as kill or killall and ps -A (to obtain process IDs for kill) that are of use (use "man <command>" in terminal to check them out & use "q" on the keyboard to quit the man program itself).

However with  a gui app like computer janitor (or browsers etc) that seize, I like to use the force quit button on the panel. To add it to the panel, right click the panel and "Add to panel" "Force Quit".

When a graphical app like computer janitor locks up, click on the Force Quit button on the panel and your mouse cursor will change into a cross. Locate the cross over the seized app window and left click, then select Force Quit. Hitting Esc button at any time your cursor is a cross, will switch the Force Quit off.

Or alternatively use Alt + F2 and type xkill in the run dialog box. Your cursor will turn into an x and the rest is pretty much the same as for the force quit button, except to escape xkill right click anywhere to get rid of it.

---

### Post by bouncingwilf on 2010-10-12
Well I'm sure I'm about 100 years behind the times but a certain way of getting an app stopped is with kill. thus;

open a terminal and type ps -ef ; this will give you a list of all running processes together with their process ID's;

Note the PID of the process you wish to stop and type

kill -9 PID (insert the PID number here)

That should do it - man kill will give you more info on the process if you need it.

Bouncingwilf

---

### Post by Ctrl-Alt-F1 on 2010-10-12
If you are looking for something GUI based then System > Administration > System Monitor contains a tool.

Just click the "Processes" tab on the system monitor.  Then you can see processes and click the end process button to kill them.  If the program isn't listed you can try using the view menu and setting it to "all".

If your graphical user interface isn't working you can log into a virtual terminal by hitting Ctrl-Alt-F2 (ctrl-alt-f8 to return back to the gui) and inputing your login credentials.  The tool "top" can be useful for diagnosing problem processes from the cli.  You can also try "ps -A | grep ****" where **** is the name of a program.  This will show only the processes containing the name of the program you "grep".  ps -A will show all processes.

You can then use the PID in conjunction with the kill command to bring a program down.  For example on my machine the program "nano" has the process id (pid) of 4669.  I can issue kill 4669 to end nano.

Hope this helps.  It's a lot to chew on.  The graphical method is definitely the most intuitive if its working.

---

### Post by yetiman64 on 2010-10-12
> **bouncingwilf said:**
> Well I'm sure I'm about 100 years behind the times but a certain way of getting an app stopped is with kill. thus;

open a terminal and type ps -ef ; this will give you a list of all running processes together with their process ID's;

Note the PID of the process you wish to stop and type

kill -9 PID (insert the PID number here)

That should do it - man kill will give you more info on the process if you need it.

Bouncingwilf

I would suggest that "kill -15 PID" may be a good idea for general use -- just in case the app being killed uses a lockfile (stops multiple instances of the same app running at the same time). The difference being a "-15" kill on a process (TERM signal) is intercepted by the application itself and not by the kernel as happens with a "-9" (KILL signal). 

If a lockfile is used and the program is not coded the best, then the mess left behind with a "-9" signal can leave the application unusable till the offending lockfile is hunted down in the filesystem and deleted (easy enough to do generally, but can be a bit daunting for some, particularly beginners).

Having said that, bouncingwilf's suggestion will work still, but on odd occasions may lead to further problems as described above.

Edit: always seem to forget System Monitor here, very useful tool for what you want to do :).

---

### Post by muteXe on 2010-10-12
+1 to post #4 - grepping the output of your ps gives you exactly what you need to see, and no more than that.

---

### Post by Legeril on 2010-10-12
Thanks a lot guys, lots of information there and as always its a great help. There are a few methods there, I'll add a force quit button as it seems the easiest for me to understand right now =)

I'm marking this thread as [solved] you've all been a great help

---

