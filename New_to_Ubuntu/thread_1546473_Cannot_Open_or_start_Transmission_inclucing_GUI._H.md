---
title: "Cannot Open or start Transmission inclucing GUI. Help needed."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by scrypt on 2010-08-05
Hello all.

I have been running Transmission flawlessly up until today.
I can no longer open or Run tranasmission. When I click on the Transmission Icon on my top panel nothing happens.
I then try to open Transmission again by clicking on the same icon. I then get an error message that says:

Transmission cannot be started.
Transmission is already running, but is not responding.  To start a new session, you must first close the existing Transmission process

I have uninstaled and reinstalled Transmission through Synaptics. but this did not fix the issue.
Does anybody have A fix. Or know how I can fix this problem.

Thanks in advance

---

### Post by What Rights on 2010-08-05
Have you killed the process in System Monitor?

Kill the process, Reboot, Remove, Update apt, Reinstall, Reboot, Run?

---

### Post by scrypt on 2010-08-05
Hello what rights

I cannot seem to close all the transmission entries in System monitor. I could stop on transmission entry. But the second one changed its status from sleeping to running to stopped and now it is stuck on Zombie and I cannot End Process.
It is also using 98-100% of my CPU.
I also cannot kill process by using Killall transmission in terminal

---

### Post by scrypt on 2010-08-05
I really need help with this please

---

### Post by da burger on 2010-08-05
In a terminal,
```
top
``` and look at the PID for transmission.

Then ```
kill <PID>
``` (replace <PID> with the actual PID of course)

If that doesn't work ```
kill -9 <PID>
``` should get it.

EDIT Also I assume this isn't the problem as this wouldn't cause zombie processes and 100% CPU usage, but it isn't open in the tray is it? Cause a couple of program do that...

---

### Post by scrypt on 2010-08-05
Thanks for the reply.

I have also noticed when viewing system monitor that winecfg.exe is also still running and cpu id 75-80%. even though I closed wine down.

There seems to be some serious problem here i really would like to help to get fixed and learn what is the problem

I also used the commands you gave me and the output they give says not valid

---

### Post by scrypt on 2010-08-05
okay i used top command and it opened all the running processes in terminal.

I then clicked "k" to type kill and it showed "PID to kill:"  I then typed in transmissions PID which is 8215. it then showed: "Kill PID 8215 with signal [15]:" I typed "Y" for yes. But it did not kill transmission process.

But the above did work for winecfg.exe. it usccessfully killed the winecfg.exe process.

> EDIT Also I assume this isn't the problem as this wouldn't cause zombie processes and 100% CPU usage, but it isn't open in the tray is it? Cause a couple of program do that...

No transmission is NOT open on my tray

---

### Post by da burger on 2010-08-06
Oops, you need to hit 'q' to leave top before the last couple of commands work.

---

### Post by scrypt on 2010-08-08
Hello

I am still having trouble with transmission. When I start it transmission the GUI appears. But it is Greyed out. and will not start correctly. I cannot use transmission because of this.
System Monitor shows transmission is stuck in sleeping status.
I have uninstalled transmission using synaptics. re-started Ubuntu and reinstalled. but the same problem re appears after Ubuntu re-start. I am using Ubuntu 10.04 (Lucid Lynx)
How can I fix this issue. Can anybody help with this?

---

### Post by scrypt on 2010-08-08
I Still cannot use transmission.

To try to fix this issue I have emptied my Downloads Folder of all Files that transmission created. I then open Synaptic and completely remove all packages related to transmission. transmission-common. transmission-gtk etc. But this for some reason. does not fully uninstall all transmission dependencies. After fully un-instaling transmission. I re-start Ubuntu. and re-install transmission. But when I start transmission I still get the same problems. GUI Freezes. Greys out etc etc.
Becuase. When I run:

sudo aptitude install -f

It gives me this output:

mark@mark-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following NEW packages will be installed:
  transmission-common wine
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/234kB of archives. After unpacking 672kB will be used.
Do you want to continue? [Y/n/?]

This is really bugging me. I would really like to know why this is happening. and how I can fix this.
Can anybody clarify why this is happening

---

### Post by scrypt on 2010-08-08
Also if I leave transmission open for some time. I can No longer close it using system monitor or xkill command etc.
It also stays in Zombie status and CPU usage is 98-100%

---

