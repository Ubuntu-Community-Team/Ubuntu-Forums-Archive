---
title: "Run command at interval"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-02-21
i'm trying to run a command every 15 seconds.  
the command is ```
pkill feh&&feh -g 70x70 $(dcop amarok player coverImage)&
```
which is intended to display the current amarok album art in a small box.
i tried ```
watch -n 15 'pkill feh&&feh -g 70x70 $(dcop amarok player coverImage)&'
```
that'll launch the one feh, but wont kill and restart it every 15 seconds as i specified.  what am i doing wrong?  or is there an easier way to accomplish my goal?

thanks in advance for any and all help.

---

### Post by ibuclaw on 2009-02-21
There is an alarm-applet for Gnome that, as far as I'm aware, is capable of running commands at repetitive intervals: [https://launchpad.net/~joh/+archive/ppa](https://launchpad.net/~joh/+archive/ppa)

Else, you could always put what you are doing in a script and include it in a your crontab.

Ensure that you include:
```
DISPLAY=:0
```
though, else the cron won't appear to work.

Regards
Iain

---

### Post by llamabr on 2009-02-21
This is untested by me, but I think your:

feh&&feh

Should read:

feh && feh

In order for bash to read the &&'s, it will need the space between the feh commands.

hope it helps.

---

