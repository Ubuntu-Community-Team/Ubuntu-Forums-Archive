---
title: "Basic bash script - using &amp;"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by lemuriens on 2011-01-25
Hi all,

I wrote a basic bash script, part of which includes the line

```
sleep 10m && notify-send "message"
```

I used update-rc.d with "default" to make this run on startup. The sleep command runs fine, but the notify-send command doesn't run.

What's the deal yo?
Thanks!

---

### Post by Brandon Williams on 2011-01-25
I suspect that the problem is related to getting dbus access. The environment is probably missing important variables when you attempt to run notify-send. Try adding "2> /tmp/notify-send.err" to the end of the notify-send command line, and then check /tmp/notify-send.err after the script has completed its run in order to see any errors output by notify-send.

---

### Post by Jose Catre-Vandis on 2011-01-25
Does notify-send need the GUI? Have you tried the script in your startup session so that it can run after gui login / desktop?

---

### Post by Cheesehead on 2011-01-25
It probably *is* working. The scripts in rc.d run as root. Root is indeed probably being notified 10 minutes after startup.

Try:
```
DISPLAY=:0.0 sudo -u YOURUSERNAME notify-send 'message'
DISPLAY=:0.0            #tells the system which display you are using
sudo -u YOURUSERNAME    #tells the system who to send the notification to

```
You might only need the DISPLAY=:0.0 variable, or only the sudo -u to run the script as you instead of root, or you might need both. Let us know if one of those works!

---

