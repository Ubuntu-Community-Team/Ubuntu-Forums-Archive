---
title: "Launching X apps from cron"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by 655 on 2010-01-21
I know this has been asked a million times, but still I don't know why this cron job is failing.  I presume it has to do with the fact that I'm trying to launch an X application from cron.

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin:
DISPLAY=:0
# m h  dom mon dow   command

27 18 * * * echo "test" > /home/me/test
29 18 * * * /usr/bin/Xdialog --title Shutdown --no-buttons --infobox "Shutting down, save your work." 6 35 180000 && /usr/sbin/shutdown -h now
```

As you can see, I set the display variable to 0 which I believe should be the current desktop (only one screen).

The first command executed correctly and generated a test file.
The second one does not!  The job is listed in the jobs list and the daemon is running.

Any help would be appreciated.

---

### Post by 655 on 2010-01-28
Bump - any thoughts?  Thank you!

---

### Post by freak42 on 2010-01-29
it's a tricky field, at least something I haven't fully understood yet.

but try playing with the display variable:

for instance if I go to a non-x console with ctrl-alt F2:

$ xeyes
Error: Can't open display.


so try setting the x-display to your local display:
$ export DISPLAY=:0
$ xeyes

does open the xeyes window on my regular x-window system. (I think you need to be the same user in both sessions, so it might still fail starting it with cron :( )

you might get more info from here [http://ask.metafilter.com/76470/Remotely-starting-local-X-application](http://ask.metafilter.com/76470/Remotely-starting-local-X-application) or by googling X and display and stuff.

hope this pushes you in the right direction

matthias

---

### Post by 655 on 2010-02-17
Setting display to 0 or 0.0 doesn't seem to have changed the functionality.

Help!

---

### Post by ayenack on 2010-02-17
Try this small change.

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin:
env DISPLAY=:0
# m h  dom mon dow   command

27 18 * * * echo "test" > /home/me/test
29 18 * * * /usr/bin/Xdialog --title Shutdown --no-buttons --infobox "Shutting down, save your work." 6 35 180000 && /usr/sbin/shutdown -h now
```

If that doesn't work try this.

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin:

# m h  dom mon dow   command

27 18 * * * echo "test" > /home/me/test
29 18 * * * env DISPLAY=:0 /usr/bin/Xdialog --title Shutdown --no-buttons --infobox "Shutting down, save your work." 6 35 180000 && /usr/sbin/shutdown -h now 
```


If you have more than one display it'll be DISPLAY=:0.0 To display on first monitor.

Also make sure that all the paths are correct and that all are included.

---

### Post by 655 on 2010-02-17
Your first code didn't work, because env at the top confuses the cron file syntax and it throws a 'bad minute' error.

No errors with putting env inline, but the app is still not loading.  I confirmed that running that path from the command line does launch the window as needed.

To be honest, I don't truly understand the functionality of the PATH: variable at the top.

---

### Post by 655 on 2010-02-17
Okay, I put this into my local user crontab instead of the root crontab and it fired correctly.
The notification Xdialog, that is.

The problem is, I want to call for a shutdown at the same time, and as I understand I need sudo/root permissions to do that.  Which is why I was putting it in the system-wide crontab.

---

### Post by ayenack on 2010-02-17
Just put the shutdown in root crontab and make it run at the right time.

---

### Post by 655 on 2010-02-19
Did the trick, thank you!

---

