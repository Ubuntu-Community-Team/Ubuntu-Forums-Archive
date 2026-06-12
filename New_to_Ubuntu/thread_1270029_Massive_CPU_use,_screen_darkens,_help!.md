---
title: "Massive CPU use, screen darkens, help!"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by john wagner on 2009-09-19
I'm running 9.04 on a laptop (4 gig ram, 160 gig HD) and have a problem.  If I open five or six windows, my laptop stops.  The screen darkens to grey, everything freezes.  I click on my system monitor and it shows 80-90% cpu usage.  I open it to see what programs are running, and it's just firefox.  WTF!?!
This all happened after I reloaded 9.04 (after a re-format).  Clean install.  Same cd I used the first time.  Now I get the lockups and none of my video's work.  Stuff that played fine before, doesn't even start now.  I try to reload FLV (for example) and I'm told a newer version is allready installed.  WTF?!?!  Something had to have come in on an update, that's all I can figure.
Is there a site I can go to for the earliest stable version of 9.04 and do a clean install of that?
Getting very frustrated here!  Nothing is working correctly.  Heck, I may go back to my Dapper!
john

---

### Post by yeats on 2009-09-19
There is a great command-line tool called top.  You invoke it the terminal by typing:

```
top
```

Up will come a list of all the programs running, with the biggest resource consumers on top.  It shows memory and CPU usage and updates every second.  It is not recommended to kill processes randomly (especially without trying to kill a program the "right" way first), but you can type "k" followed by the process ID (pid) for stubborn programs that won't die.

The other suggestion is to run Firefox from the command line in safe mode:

```
firefox -safe-mode
```

This will disable all add-ons, which will let you know whether the problem is Firefox itself, or something you have added on (like Flash) that is causing the problem.

There are many threads in the forums and pages on the web about Firefox CPU problems.

---

### Post by john wagner on 2009-09-19
What are these two items?

10204 messageb  20   0  2984 1344  812 S    0  0.1   0:00.59 dbus-daemon 
       
10552 haldaemo  20   0  6712 4572 3764 S    0  0.2   0:00.57 hald      


john

---

### Post by shae on 2009-09-19
I think that firefox is probably the cause of your problems.  Do you use a lot of extensions?  Have you tried a different browser like midori or opera to see if you still have those problems?

Furthermore, have you tried with compiz disabled to see if you have as many programs crash?

---

