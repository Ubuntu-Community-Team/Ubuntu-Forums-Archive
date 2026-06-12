---
title: "Which log will help for problem solving?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Irishpolyglot on 2010-04-11
I'm having several problems with my Ubuntu of late; All of Gnome randomly crashes me to the log-in screen and I lose whatever I'm working on instantly, and separate to that boot up takes an incredible 8 minutes to log-in screen. So I'll write to this forum for help on each of the issues separately.

I remember when asking for help before that I had to give a log file, but in 9.10 the layout seems to have changed and there are a huge number of log files on the left of the screen. Which one(s) should I copy the recent part from to help solve such issues?

Many thanks!

---

### Post by jvc26 on 2010-04-11
Difficult to say really, I'd try:

Xorg.0.log
Syslog
debug

May be of use - have a look whether you're getting errors sent to them around the time stuff is booting up.

Also, as you start up the machine, press Ctrl+Alt+F1 to drop you to a console tty. Then watch that to see whether errors are getting logged to that at boot while its loading up. You may find the 8min startup is because its trying something and failing repetitively.

Il

---

### Post by lidex on 2010-04-11
> **Illuvator said:**
> Difficult to say really, I'd try:

Xorg.0.log
Syslog
debug

May be of use - have a look whether you're getting errors sent to them around the time stuff is booting up.

Also, as you start up the machine, press Ctrl+Alt+F1 to drop you to a console tty. Then watch that to see whether errors are getting logged to that at boot while its loading up. You may find the 8min startup is because its trying something and failing repetitively.

Il

In a terminal:
```
dmesg | less
cat ~/.xsession-errors
```

---

