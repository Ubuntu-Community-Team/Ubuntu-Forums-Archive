---
title: "ISO QuicKeys-like automation program for Ubuntu desktop"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by watchpocket on 2009-10-25
I'm wondering what might be the closest thing to the MacOS Quickeys program that one could use on the Ubuntu desktop.  QuicKeys allows you to automate all sorts of tasks.

I'd be using such a program for daily auto-logging into several shell windows on 2 or 3 different ISPs via SSH, and perhaps to open Firefox at the same time on the desktop, as well as for any other things one might want to automate / expedite.

Thanks in advance for any suggestions.

---

### Post by martrn on 2009-10-25
> I'd be using such a program for daily auto-logging into several shell windows on 2 or 3 different ISPs via SSH, and perhaps to open Firefox at the same time on the desktop, as well as for any other things one might want to automate / expedite. Thanks in advance for any suggestions.

```
sudo apt-get install gnome-schedule
sudo apt-get install kcron
```

[URL="http://docs.kde.org/stable/en/kdeadmin/kcron/index.html"]
http://docs.kde.org/stable/en/kdeadmin/kcron/index.html[/URL]

Unix and unix-like systems (for which OSX is one), have have used contrab for quiet a period of time during history to automate several tasks on the computer.  Unix was originally written as a multi-user OS.

GNU/Linux is used world-wide for a lots of servers, and contrab or software to run cron jobs have been at the heart of the OS since its inception. Finding a gui application to control cron jobs should be no difficult feat.

[http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/]("http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/")

---

### Post by watchpocket on 2009-10-26
cron -- of course.  Little experience with it so far, but I do know about it.  I'm getting a System76 Wild Dog box in few weeks & it'll be my first time using GNU/Lnux on the desktop.  Up to now I've run NetBSD and FreeBSD only, and only via ssh.  Thank you very much for the info & links.

---

