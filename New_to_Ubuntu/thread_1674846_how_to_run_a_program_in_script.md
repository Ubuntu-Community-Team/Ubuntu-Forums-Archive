---
title: "how to run a program in script"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by joesto1 on 2011-01-24
hi all
when i am in terminal and type the name of a program the program starts to run, so if i want to start the same program from a script do i have to know where the startup program is or will the program name be enough?

if a program says it cannot be run as root how do i change back to usr after using 
sudo -i
thanks
joe
;)

---

### Post by sohail_linux on 2011-01-24
either put that program(binary) in default path e.g /usr/bin , and then call it just by its name from script , or call it by its complete path. when u r running something with sudo , only that program(binary) will be running with root permission ,not everything comes after that.

---

### Post by bodhi.zazen on 2011-01-24
> **joesto1 said:**
> hi all
when i am in terminal and type the name of a program the program starts to run, so if i want to start the same program from a script do i have to know where the startup program is or will the program name be enough?

It depends on the script and how you call it, but it is best to use the full path.

If you are calling a program more then once, use a variable

IPTABLES='/sbin/iptables'

> if a program says it cannot be run as root how do i change back to usr after using 
sudo -i
thanks
joe
;)

Well, with sudo.

```
sudo -u user program
```

See man sudo

---

### Post by joesto1 on 2011-01-24
thanks will try this
thanks
joe

---

### Post by joesto1 on 2011-01-24
hi 
what am i going wrong?
i wrote a script called it t.sh
this is the script


#!/bin/sh
#Script to check if the teamviewer are running.
#Script is written by joesto1
process=`ps auxwww | grep teamviewer | grep -v grep | awk '{print $1}'`
if [ -z "$process" ]; then
echo "Couldn't find teamviewer running Restarting teamviewer "`date` >>/var/cccamlog/team.check
[COLOR=Red]teamviewer[/COLOR]
else echo "[COLOR=Red]teamviewer[/COLOR] is still OK!                            "`date` >>/var/cccamlog/team.check
fi 
i run a crontab every 5mins to exicute this script and the log file is updated  but the program teamviewer does not start WHY?

but is i run this script from terminal it start the program[COLOR=Red] teamviewer[/COLOR] ok WHY ?
thanks
joe

---

### Post by bodhi.zazen on 2011-01-24
cron runs with a minimal environment and you did not use the full path to teamviewer (and other binaries) as I advised :twisted:

This is probably the #1 FAQ with cron.

---

### Post by joesto1 on 2011-01-24
hi 
thanks for the quick reply
the program is in apps/internet/teamviewer

i am very new to linux but keen to learn
in terminal if i type 

ps -ef | grep teamviewer 

when teamviewer is running is returns

/opt/teamviewer/teamviewer/5/wine/bin/wineserver

i have tried to use this line but still not running 
any ideas
thanks
joe
;)

---

### Post by bodhi.zazen on 2011-01-24
Open a terminal and enter 

```
which teamviewer
```

Are you running it with wine ?

In that case, the command may need to be

/path/to/wine /path/to/teamviewer.exe

---

### Post by joesto1 on 2011-01-25
thanks bodhi.zazen

when i enter which teamviewer it returns
/usr/bin/teamviewer


si i put that into my script but still no restart of teamviewer but the log is updated
thanks
joe

---

