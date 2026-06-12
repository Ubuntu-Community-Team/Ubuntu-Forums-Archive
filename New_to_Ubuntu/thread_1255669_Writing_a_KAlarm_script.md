---
title: "Writing a KAlarm script"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-09-01
Hello,

I'm working on setting up an alarm system on a computer running Ubuntu 8.10.  I heard that KAlarm works great, so I downloaded it.  Now I'm stuck trying to figure out how to write a script that runs a music file at a specified time.  Thanks in advance!

-Val

---

### Post by Prince Valiant on 2009-09-03
Anyone?  I just need a way to play a music file at specific times.

---

### Post by unutbu on 2009-09-03
Perhaps you do not need a script. You could use a command like this:
```

cvlc /path/to/music/file

```
cvlc is a command-line tool provided by the vlc package. Any command-line program that plays music files will do. There are probably more of those than you can shake a stick at...

---

### Post by KIAaze on 2009-09-03
And then you can use "cron" or "at" to run such a command at a specific time:
[http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html](http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html)
;)

-"cron" is for regular events.
-"anacron" is also for regular events, but makes sure the command is run at next boot in case the PC was off when it should have run.
-"at" is for commands to run once at a specified time.

Of course, it's quite possible that Kalarm offers an easier way to do such things, but I haven't tried it.

edit:
Just tried it, and yes, it's much easier with kalarm. :)

---

