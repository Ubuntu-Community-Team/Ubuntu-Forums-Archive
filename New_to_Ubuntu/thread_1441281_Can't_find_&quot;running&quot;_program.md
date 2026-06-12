---
title: "Can't find &quot;running&quot; program"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by agberg on 2010-03-28
Hi...

I'm using Ubuntu 9.10, and many times when I open a program I get this or a similar message:

"The system has detected that another copy of Audacity is running.
Running two copies of Audacity simultaneously may cause
data loss or cause your system to crash."

Problem is, there's no indication it's running and I can't find it. No evidence of it or link to it, either on the desktop or in the panel.
Force quit does nothing either.

Does Ubuntu have something similar to the old Ctr/Alt/Delete or F4 key to kill something? 
Thanks!

---

### Post by agberg on 2010-03-28
Sorry, I meant the Alt/F4 command.

---

### Post by Paddy Landau on 2010-03-28
Well, you can go to System > Administration > System Monitor > Processes (or you could do it via the terminal with the 'ps' and 'kill' commands).

But there's something wrong if you close Audacity, and it doesn't actually close. I know Windows does this sort of thing a lot, but it's very rare for Linux to cause this problem.

---

### Post by dwarfolo on 2010-03-28
Open a terminal and try

killall -9 audacity

this should terminate any instance of the application

---

### Post by agberg on 2010-03-28
Thanks to all for the help. I forgot about xkill...I've used it a few times before.

I'm using Audacity 1.3.9, and it frequently vanishes from the screen but is still running.

I've "narrowed" it down to either Audacity (I think this is a beta version) or, more likely, it's a PBKAC -- perhaps the way I have Audacity or Firefox configured when switching between programs.

---

### Post by PocketDog on 2010-03-28
Audacity is brilliant, but buggy. As you know. I don't think it should be v1.*.. yet.

In Terminal, type ```
top
```It's the fastest way to see your running processes. It has the PID of anything you need to kill and it's installed by default too.

---

