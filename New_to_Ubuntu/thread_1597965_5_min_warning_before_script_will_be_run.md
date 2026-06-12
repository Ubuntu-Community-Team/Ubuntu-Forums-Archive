---
title: "5 min warning before script will be run"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-15
i use the following script to turn off my computer at 10. my daughters bedtime during the school week
how do i modify this so that i can add a 5 min warning before the shutdown script is run. that way my daughter can save anything she is working on


#!/bin/bash
notify-send "Good Nite Kat-computer will shutdown at 10pm" -t 10000
sleep 10s
echo xxx | sudo -S shutdown -h 21:57
notify-send "The script has finished"
tks

---

### Post by earthpigg on 2010-10-16
make another script that runs at 9:55 pm?

---

### Post by john newbuntu on 2010-10-16
I can sugggest a slightly different way if you are prepared to use zenity and
cron.  Create a script such as this one(say /home/user/.logout.bash):
```
#/bin/bash
(
    echo "# System shutting down in 5 minutes"
    sleep 300
) |  zenity --progress --title="SHUTDOWN" --pulsate --no-cancel --auto-close

/sbin/shutdown -h now
exit 0
```Then run the command "sudo crontab -e" and add the following line:
55 21 * * * env DISPLAY=:0.0 /home/usr/.logout.bash

If you are not able to see the zenity screens, log in as root using "sudo su"
and edit the file ".profile".  Add this command towards the end:
```
xhost +LOCAL:
```

---

### Post by rburkartjo on 2010-11-16
earth used your suggestion. works great tks

---

