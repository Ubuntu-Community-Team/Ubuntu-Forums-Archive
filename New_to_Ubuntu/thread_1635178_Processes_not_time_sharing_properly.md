---
title: "Processes not time sharing properly"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-01
I was downloading the Ubuntu updates and then I went into Firefox to check my mail on a mail web server. Normally it takes about 5-7 seconds for the web server to authenticate my pw and username, but with the download going on, it took from 4 to 5 minutes. 
 When I am using XP, it also takes about 5-7 seconds for the mail web server to authenticate and if I am downloading something at the same time, it takes, maybe, 15-20 seconds for the mail web server to authenticate.

Question: I know there must be some setting in Ubuntu to allow other processes that have the focus to have more time-slices, but don't know how to do it.
    
I have noticed this also using Firefox, when I am downloading something from YouTube and I open up a new tab to go to another web site. The new opened tab slows down to a crawl.

---

### Post by MG2R on 2011-02-06
You could try altering the nice-value of the processes involved. nice is the equivalent to the priority of a process in Windows. If a process is less nice, it gets e higher priority...

You can change the nice-value of a process by going into the System Monitor (Under System>Administration>System monitor. Or go into a terminal and enter the command gnome-system-monitor). Click on the Processes tab, right click on the process you want to alter and select 'Change priority...'.

---

### Post by firebird_1979 on 2011-02-06
This can have multiple reasons though, possibly not caused by Ubuntu.

-Your email provider might have been very busy
-Your internet connection might have been at it's throughput limit (were you downloading stuff?)
-Some other process might take up most of your computer's resources

Without some more information it's hard to say what caused your login to take 5 minutes. I would suggest you try logging in again, but have System Monitor run on the foreground ("always on top" setting enabled for it's window).

This way you can see which process takes up all your CPU cycles, if your Internet connection is bogged down etc.

---

