---
title: "Creating crons from java/jsp"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2009-01-26
Hi!

I was wondering if it was possible to create a cron tab (which would then call a java applet at a specific time) from within a java class or JSP page running on Ubuntu. Without going into too much detail, I have a program where a user can schedule an event, and when that time has been reached, that event starts up.

Any suggestions for scheduling would be most welcome, though the easier to implement, the better, as I am in a bit of a time crunch.;)

Thanks!

---

### Post by blueridgedog on 2009-01-26
Crontab and the way to schedule tasks was just brought up in this thread:

[http://ubuntuforums.org/showthread.php?t=1050220](http://ubuntuforums.org/showthread.php?t=1050220)

Much of it applies to what you are trying.

---

### Post by punong_bisyonaryo on 2009-01-27
Thanks! I knew about crontab, but actually the problem is how do I make cron jobs from Java?

---

### Post by blueridgedog on 2009-01-28
From this site:

[http://groups.google.com/group/comp.unix.solaris/browse_thread/thread/60a882c9e3ba1daa](http://groups.google.com/group/comp.unix.solaris/browse_thread/thread/60a882c9e3ba1daa)

I obtained the following:

If you are trying to do this from a script,
1. dump the content of the existing crontab to a file
  # crontab > /tmp/dump
2. echo "your lines" >> to the corntab file
  # echo " 00 1 * * * /monitor_file_system  2>/dev/null" >> /tmp/dump
3. import the new crontab
  # crontab /tmp/dump 

If you can do file manipulation in java, then you can approximate those steps.

---

