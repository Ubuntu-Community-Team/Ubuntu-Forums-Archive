---
title: "100% CPU always - Fixed it - Here's how"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by duetome on 2011-05-30
Hello Kids,

Last Line in:
/etc/init.d/rcS - **this 1.** is what was on my computer when I installed the Ubuntu 10.10
                          
  1. Wrong:         exec  /etc/init.d/rcS

  2. CORRECT:** exec  /etc/init.d/rc S**


I had added the Avast line about this and noticed  that my CPU was at 100% all the time. I was getting PID entries in my System Monitor -Processes with different code numbers.

Thinking it was Avast that was causing it.  I removed the following line and replaced it with another entry I found on the Internet.

removed - sysctl -w kernel.shmmax=128000000
replacement line was:
echo 128000000>/proc/sys/kernel/shmmax

This did not fix the high 100% CPU usage. It did fix the scrolling shmmax=128000000 on the
start up screen.
After spending the weekend staring at the screen I notice something from a website on how to enter the sysctl...... that ---**linuxgeek77** had entered for fixing Avast.   

That's when I noticed that my computer came with the line 1. 
So I changed it to:** exec  /etc/init.d/rc S**  at the bottom of the page and saved it.

 Restarted the computer and that fixed the 100% CPU problem right away.
So is this something that just happen to my computer? Or is this a typing mistake that is causing all kinds of problems that I see on this site. You may want to check your rcS  file.

sudo gedit  /etc/init.d/rcS
Remember the last entry at the bottom should look like this:
**exec  /etc/init.d/rc S**
PS: does this get me another bean if it is a fix for you?
duetome

---

