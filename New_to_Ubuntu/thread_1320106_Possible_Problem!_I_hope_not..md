---
title: "Possible Problem?! I hope not."
date: 2009-11-08
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-11-08
OK I need a bit of help fixing something. I got these messages after running rkhunter:

1.     /usr/bin/wget                                            [ Warning ]

2.    /usr/sbin/unhide                                         [ Warning ]

3.    /usr/sbin/unhide                                         [ Warning ]

4.    Checking for running syslog daemon                       [ Warning ]

5.    Checking /dev for suspicious file types                  [ Warning ]

System checks summary
=====================

File properties checks...
    Files checked: 127
    Suspect files: 3

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 1 minute and 22 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)





Should I be [slightly] worried? What's the best way to fix these problems. I have tried going into the  (/var/log/rkhunter.log) but I keep getting denied.

Is there anything?

---

### Post by Rayve on 2009-11-08
Are you getting denied because you don't have permission to view the file?

You should be able to enter the following and see the file [don't make any changes if all you want to do is view it! if you do make changes, make a backup of the file first!]:

```

sudo gedit /var/log/rkhunter.log

```

You will then enter your password when the terminal prompts (you won't see your typing show up), and then you should see the /var/log/rkhunter.log file appear in a text editor.

---

### Post by 289531.EXE on 2009-11-09
I saw the log (thanks!) but what do i do  now? it has a bunch of stuff and a few things were "whitelisted" and a few other "suspicious files" were  there.

---

