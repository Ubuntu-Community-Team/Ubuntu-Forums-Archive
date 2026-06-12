---
title: "Problems after update"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Stargazer777 on 2009-04-28
I updated my computer from 8.04 to 8.10. After my computer runs for about 15 minutes, it restarts. Does anyone know how I can fix this?

---

### Post by hesjnet on 2009-04-28
Sound very strange. Are you sure that this is not caused by a program that you are running? Maybe try to boot up your computer and try to leave it alone for 15 minutes and see if it still happens.

---

### Post by OffAxis on 2009-04-28
what do you mean by 'restart'?

Does the system drop immediately to the BIOS and Post or does ubuntu act like you hit the Restart button (suspend the session, unload everything, power down, and power up)?

---

### Post by wwusnobrdr on 2009-04-28
I suggest you take a look at the log files.  If you click Administration>Log File Viewer you can view these easily through a graphical interface.  I would check the messages and syslog around the time the system restarted.

---

### Post by lovinglinux on 2009-04-28
This sounds like a hardware problem. I had this problem a few months ago while using Windows and I discovered that there was a melted down component on the motherboard. It was really bad, but the computer still worked for weeks, with these restarts now and then.

Faulty memory could also be the problem. There is a tool for testing the memory in your Ubuntu Live CD. Boot from it and choose the memory test.

---

