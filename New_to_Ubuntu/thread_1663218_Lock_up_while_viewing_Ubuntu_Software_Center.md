---
title: "Lock up while viewing Ubuntu Software Center?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by beringse on 2011-01-09
Hi-quick question...I've been using 10.10 with virtually no hassles for a few weeks until this AM while I was looking at software listed in the center. I clicked on a screenshot and my system ramped up to 100% CPU usage and locked up. 3GiB memory on the machine so I really do not think that lack of memory is the issue.

Has anyone had something like this happen before, and how do I refrain from doing a hard reset? I tried the Ctl-Q and a few others but the box was locked solid. Thanks for the input

---

### Post by TeoBigusGeekus on 2011-01-09
Whenever something hangs, open a terminal and
```
killall nameofapp
```
in your case
```
killall software-center
```
Alternatively, you could press Alt+F2 and give the same command or just add the Force Shut Button on one of your panels.

To investigate what's causing all this high cpu/ram usage in software center, open it via command line
```
software-center
```
and post us any error messages you see when the application crashes.

---

### Post by beringse on 2011-01-09
Thanks for the info on commands, didn't know about those particular ones. Bad thing about when the box locked up nothing was working-keyboard/mouse were unresponsive Even tried talking to it, ha...
I'll post if it happens again, hopefully this was a fleeting glitch.

---

### Post by beringse on 2011-01-10
Well, it did it again, locked up solid-could not reboot with key commands. I opened up software center via the terminal after the forced shutdown and got this message: 
2011-01-10 06:51:08,729 - softwarecenter.app - INFO - software-center-agent finished with status 1
Not quite sure if this has any bearing on what happened, but as it is I'm not going to use the software center until I get this figured out.

---

