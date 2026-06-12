---
title: "I'm having some trouble with a script under a cron"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by roscowgo on 2009-09-26
Hello all, I just installed xubuntu 9.04 last night.  Been fiddling with the eye candy portion of the show, my last little twitch is trouble with the backgrounds.  

I found a script that executes and causes my backgrounds to cycle according to the image list under desktop settings.  I just can't get it to run from a cron though.  I'd rather use drapes or wally, both of those run but never manage to actually change the background.  At any rate the only errors I've been able to see are under webmin when I do a run now on the cron.  Here they are, (same error when ran as me and root).

Output from command /home/willg/change.sh ..

** (process:7482): CRITICAL **: Failed to init libxfconf: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.



** (process:7484): CRITICAL **: Failed to init libxfconf: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.



** (process:7486): CRITICAL **: Failed to init libxfconf: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


The script itself contains this, and is marked as able to be executed. Works with no trouble with a double click, or when ran from the terminal.

#!/bin/sh
MONITOR=${1:-0}
PROPERTY="/backdrop/screen0/monitor${MONITOR}/image-path"
IMAGE_PATH=`xfconf-query -c xfce4-desktop -p ${PROPERTY}`
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s ""
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s "${IMAGE_PATH}"

cron.log reports that the job fires, but I don't know where to look for errors.
Sep 26 09:36:01 xubuntu9 /USR/SBIN/CRON[7450]: (willg) CMD (/home/willg/change.sh)
Sep 26 09:37:01 xubuntu9 /USR/SBIN/CRON[7495]: (willg) CMD (/home/willg/change.sh)
Sep 26 09:38:01 xubuntu9 /USR/SBIN/CRON[7521]: (willg) CMD (/home/willg/change.sh)
Sep 26 09:39:01 xubuntu9 /USR/SBIN/CRON[7547]: (willg) CMD (/home/willg/change.sh)


Thanks much if anyone has any suggestions or sees what i'm doing stoopid.

---

### Post by hailtothethief on 2009-09-27
The problem is that the script is being run in a session that isn't running a dbus (or even an X server, for that matter.)

Go here, do this (Enabling user level cron):
[https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron]("https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron")

Then restart cron:

```
sudo service cron restart
```

Then run ```
crontab -e
``` to edit your crontab and cause the script to run.


Make sure you **do not** run that as root, otherwise you'll just be editing the root crontab rather than your own.

---

### Post by roscowgo on 2009-09-27
I'll give it a whirl, thanks!

---

### Post by Lawck on 2013-03-16
Hello,

I've recently had the same problem as you did.
about  "Failed to init libxfconf: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed."

Further research has led me to this: [http://unix.stackexchange.com/questions/28463/run-a-dbus-program-in-crontab-how-to-know-about-the-session-id](http://unix.stackexchange.com/questions/28463/run-a-dbus-program-in-crontab-how-to-know-about-the-session-id)

with that I was able to run whatever I needed with no problems. In this case:

```

#!/bin/bash

dbus_session_file=~/.dbus/session-bus/$(cat /var/lib/dbus/machine-id)-0
if [ -e "$dbus_session_file" ]; then
  . "$dbus_session_file"
  export DBUS_SESSION_BUS_ADDRESS DBUS_SESSION_BUS_PID
  xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path -s "$(find ~/Pictures/wallpapers/ -type f -iregex '.*\.\(bmp\|gif\|jpg\|png\)$' | sort -R | head -1)"
fi

```

^_^

---

