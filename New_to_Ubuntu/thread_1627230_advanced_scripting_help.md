---
title: "advanced scripting help"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-21
i have this cron job and it works great. it runs once a week and saves the output to the log file


#!/bin/bash
echo xxxx | sudo -S rkhunter --check --display-logfile

notify-send "The rootkit hunter script has finished" -t 0

however if i run this from just the terminal no script

sudo rkhunter --check --display-logfile
after i enter my password the results of rkhunter stay in the terminal until i close it

i want to modify the first (the cron job) so the results also stay visible in the terminal until i close it.. can this be done and if so how/rks

---

### Post by rburkartjo on 2010-11-21
note i add this line before the notify send

sleep  -1

is this correct/again tks

---

### Post by rburkartjo on 2010-11-21
update had to change to sleep 9999

---

### Post by paulsarmiento on 2010-11-21
Hi rburkartjo,

I assume that the script run correctly. try redirecting the results of rkhunter to a file or use 'tee' command and see if it's there.

I experienced that running the 'notify-send' or probably any program that access the GUI session from the command line will be the culprit of your problem. there is a trick i used that queries my DBUS sessions (found in the forums as well) to get the correct address. 

```


#backup program is written here
...
#Querying the dbus sessions
user=`whoami`
pids=`pgrep -u $user $dbus`
for pid in $pids; do
# find DBUS session bus for this session
DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
# use it
export DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS
done;

echo -n "backup complete" | zenity --notification --listen

```

I'm not really sure if it will work for you.


Paul

---

### Post by rburkartjo on 2010-11-22
paul tks for the info it didnt make much difference for now the sleep 9999 works but i deleted the notify send part. i just like reports to be visible on the desktop after they run. easier than switching to root user and opening the log reports.

---

### Post by paulsarmiento on 2010-11-22
Hi rburkartjo,

Yes and it is what I expected. Your script runs on a background and thus it will run on a non-gui environment. If you really wanted to make the 'notify-send' program to work, you will have to find your gui session and indicate the environment to your script.

If you try running your script on gui session, let's say run the gnome-terminal on your GUI session and explicitly run your script will actually work including the pop-up program. But in contrast, if you try to run the script on one of your virtual terminals (eg. tty1) will not make the pop up to work.

I hope I didn't confused you.

Paul

---

