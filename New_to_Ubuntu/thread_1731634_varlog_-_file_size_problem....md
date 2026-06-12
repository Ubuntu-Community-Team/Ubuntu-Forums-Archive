---
title: "/var/log - file size problem..."
date: 2011-04-17
forum: New to Ubuntu
---

### Post by j*tech on 2011-04-17
I was freeing up disk space using Disk Usage Analyzer, and saw that "/var/log" is 16GB :-s!!!  I need the space, and I'm kinda worried since its so large (system problem? virus?)  

Can I delete the var log files, or is there a way to "clean" them?  Thanx,

---

### Post by Leppie on 2011-04-17
take a look at the files in the directory.
there should be many files finishing with .log.1, .log.2, etc.
those are old logs and if your system is running fine, it's safe to delete them.

---

### Post by j*tech on 2011-04-17
Ok, I see 8 files over 1GB:

*syslog, ufw.log, messages, kern.log, and 4 named the same with the .1 extension*

---

### Post by Leppie on 2011-04-17
go to System>Administration>Log Viewer, view the content of those files.
I'm confident you can remove the .log.1 files.

---

### Post by scott-ian on 2011-04-17
The log files usually aren't important.  They are however, if you have a problem and want an expert to look into it.  If you have had no such problems, the logs are unimportant.  The system will still keep logging events, adding more and more gigabytes.

---

### Post by Elfy on 2011-04-17
If you have got an issue then removing the old log files is a temporary help.

I would actually have a look and see if there's something recurring.

---

### Post by j*tech on 2011-04-17
Deleted them...Strange thing is Disk Usage Analyzer is now not working properly :neutral:...

---

### Post by j*tech on 2011-04-17
figured it out...i used ***sudo nautilus*** to delete the log files, and I guess they were put in another trash folder or something I could only access as root...So I used ***gksudo*** (I should have used this 1st :roll:) and deleted them permanately...

---

