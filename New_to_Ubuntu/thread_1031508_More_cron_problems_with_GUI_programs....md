---
title: "More cron problems with GUI programs..."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by lemuriens on 2009-01-05
I posted here a few months ago (see [http://ubuntuforums.org/showthread.php?t=974010](http://ubuntuforums.org/showthread.php?t=974010)) as I couldn't get cron to work as an alarm clock with vlc. It finally started working when I set my crontab to:
```
0 07 * * * /usr/bin/alarmclock.sh
```
and made alarmclock.sh:
```
#! /bin/bash
DISPLAY=:0 /usr/bin/vlc
"mms://wmlive-acl.bbc.co.uk/wms/radio4/radio4_nb_e1s2?BBC-UID=74a7c929ba1d1db781e46027205005eb90d10a7f104091 2444dfe8117ceae58f_n&amp;SSO2-UID="
```

One day however, this stopped working. vlc would not pop up at 7am as it had before. I used the steps from my previous post to ascertain that:
[LIST]
[*]cron will run a non-GUI program (uptime)
[*]cron will run a test script containing a command to run a non-GUI program (again, uptime)
[*]my alarmclock.sh script will run from the terminal
[*]cron will not run vlc directly (crontab: "DISPLAY=:0 /usr/bin/vlc")
[*]nor will it run other GUI programs directly (tried with firefox)
[/LIST]

I've no idea why this has stopped working (AFAIK I haven't changed anything in the cron setup) but I'm curious to find out, and on top of that, I'm fed up of having a lie-in every morning!

Anyone know what's wrong?

---

### Post by rjmoerland on 2009-01-05
You might need to set the XAUTHORITY environment variable as well, to /home/yourusername/.Xauthority. So in the script, add 
```

XAUTHORITY=/home/yourusername/.Xauthority

```

You might even need to export XAUTHORITY and DISPLAY prior to running VLC.
```

XAUTHORITY=/home/yourusername/.Xauthority
DISPLAY=:0

export XAUTHORITY DISPLAY;

```



HTH,
Robert

---

### Post by lswb on 2009-01-05
Is it possible that through logging out/logging in that you are no longer running on display :0 ?

---

### Post by lemuriens on 2009-01-05
@rjmoerland: I've tried adding those lines into my alarmclock.sh script, but still no success...

@lswb: I'm not entirely sure. Of course, the script runs in the terminal without the DISPLAY=:0, so I guess the next question is how do I ascertain/guarantee that my DISPLAY=:0?

---

### Post by rjmoerland on 2009-01-05
> **lemuriens said:**
> @rjmoerland: I've tried adding those lines into my alarmclock.sh script, but still no success...

I take it that you replaced 'yourusername' with your user name, right? (Just checking ;))

---

### Post by lemuriens on 2009-01-05
I just tried running the script again from the terminal with the new lines, and I got an error:```

Error: Unable to initialize gtk, is DISPLAY set properly?
```
So after a little more googling I've found a workaround!

I'm running vlc with the "--daemon" option and to stop it I've set a menu item that runs "killall -9 vlc".

I don't know what problem there is with gtk or DISPLAY, but I've got the desired outcome so I'm happy!

---

### Post by lswb on 2009-01-05
> **lemuriens said:**
> 

... I guess the next question is how do I ascertain/guarantee that my DISPLAY=:0?

Just open a gnome-terminal or xterm and

echo $DISPLAY

---

