---
title: "adding a message that will be displayed a few seconds before this script if run"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-09-29
since i usually go to bed before my daughter i have this script that runs at 21:57. it loads when the system starts up


#!/bin/bash
echo xxxx | sudo -S shutdown -h 21:57
notify-send "The script has finished"

i would also like to incorporate good nite kat or whatever and have it displayed before the script is executed how would i do it/tks

---

### Post by KIAaze on 2010-09-29
Don't have much time, but here are a few things that might interest you:
Time management software:
[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

Run stuff at specific times:
[http://linux.about.com/library/cmd/blcmdl1_at.htm](http://linux.about.com/library/cmd/blcmdl1_at.htm)
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

Display messages onscreen:
[http://ldots.org/xosd-guide/osd_cat.html](http://ldots.org/xosd-guide/osd_cat.html)

Two scripts I use:

remindme.sh (based on a script posted by someone on the ubuntuforums):
```
#!/bin/bash

if [ $# -ne 2 ]
then
	echo "usage : $0 <time> <message>"
	exit 0
fi

#Figure out which display we're using

#
# Ubuntu version of osd_cat does not like "host name" in front of display
#

#HOST="$(xrdb -symbols | grep SERVERHOST | cut -d= -f2)"
DISPLAYNUM="$(xrdb -symbols | grep DISPLAY_NUM | cut -d= -f2)"
#THISDISPLAY=$HOST:$DISPLAYNUM.0
THISDISPLAY=:$DISPLAYNUM.0

TIME=$1
MESSAGE=$2

#check to see if the reminders directory exists (create if not)
if [ ! -e ~/reminders ] ; then
  mkdir ~/reminders
fi

unique=`date +%F-%H-%M-%S`
reminder="reminders/reminder-"$unique

#Now output the reminder script
echo '#!/bin/bash' > ~/$reminder
echo -n 'export DISPLAY=' >> ~/$reminder
echo $THISDISPLAY >> ~/$reminder

if which osd_cat &> /dev/null; then
  echo "echo \"$MESSAGE\" | osd_cat -s 2 -c green -p middle -A center \
  -f -adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-* -d 5" >> ~/$reminder
else
  echo "zenity --info --text=\"$MESSAGE\"" >> ~/$reminder
fi

#Make the reminder script executable
chmod +x ~/$reminder

#Schedule it to run
at $TIME -f ~/$reminder
# crontab_add.sh "*/5 * * * * ~/$reminder"

```

totalnotify.sh (offers various notification methods):
```
#!/bin/bash
# different notifying methods

EMAIL="foo@bar.com"

say_func()
{
  if which festival &> /dev/null; then
    echo $* | festival --tts
  fi
}

messagebox_func()
{
  if which zenity &> /dev/null; then
    zenity --info --text="$*" 2>/dev/null
  fi
}

cowsay_func()
{
  if which cowsay &> /dev/null; then
    echo "$*" | cowsay
  fi
}

notify_knotify_func()
{
  if which knotify &> /dev/null; then
    dcop knotify default notify eventname appname "$*" '' '' 2 0
  fi
}

notify_zenity_func()
{
  if which zenity &> /dev/null; then
    zenity  --notification  --text "$*"
  fi
}

notify_notifysend_func()
{
  if which notify-send &> /dev/null; then
    notify-send "$*"
  fi
}

mailme_func()
{
  if which mail &> /dev/null; then
    echo "$@" | mail -s "$1" $EMAIL
  fi
}

# choose which methods you prefer here
echo "$*"
say_func "$*" &
messagebox_func "$*" &
#cowsay_func "$*" &
#notify_knotify_func "$*" &
#notify_zenity_func "$*" &
notify_notifysend_func "$*" &
#mailme_func "$*" &

```

Usage:
```

remindme.sh 10:15 "Good night"
totalnotify.sh "Good night"

```

---

