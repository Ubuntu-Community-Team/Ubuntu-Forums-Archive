---
title: "starting X application from non - X screen"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by freak42 on 2009-01-19
Hello,

I have a problem poking around with mythbuntu and suspend.

I have a script that removes kernel modules and shuts down the mythbackend server and suspends and after waking up restarts everything nicely.
However it also restarts mythwelcome which is a x application (a windowed application), when I test this script from a normal console within my x session everything works fine), but when the script is run from the mythbackend server it is not within a x session and the start of the application fails. 
So is there a way of starting the application in the context of the x-session from a non x-session script?

many thanks in advance

matthias

---

### Post by yeats on 2009-01-19
I think you'll get better help in the "General Help" section.  Shell programming and kernel modules are a little beyond the "absolute beginner" category.  :-)

---

### Post by freak42 on 2009-01-20
You are right, Chris.

Luckily I found a solution to my problem elsewhere: 
So instead of simply starting the app in my non-x script```
...
app
...
```

I must set a display variable (?) and execute the app as the xorg session user
```
...
DISPLAY=:0.0 su xuser -c 'app'
...
```

where 'xuser' is the normal user which ubuntu autostarts. Of course the script must have the rights to execute stuff as this user, but in this case it's not a problem.

If someone knows a more elegant way or can explain me what really is going on here, please do. 
But I mark as solved for now. EDIT: I can't find the mark as solved button? Is it me or is it gone?

---

### Post by jonnybignote on 2009-10-19
matthias

wondered if you would mind expanding on your successful attempts at mythbuntu working with suspend.  I have Mythwelcome shutting down and restarting the system successfully, thanks to this thread

[http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)

This is a shutdown routine but I'd like to have it work with suspend.  I've configured pm-utils to unload my dvb-cards prior to suspend and when called manually, suspend works ok - machine resumes and mythtv works.  I have replaced the shutdown command in mythwakeup with 

gnome-power-cmd suspend
This does not work.  After successfully setting wakeup times and pre-shutdown checks, Mythwelcome countdown resets.  

Mythbackend.log states

Suspending
Failed to open connection to "session" message bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error:

I'm either putting the suspend command in the wrong place, or I'm completely on the wrong path and there is more to do to make this work.

Any help would be greatly appreciated

Jonathan

---

### Post by jonnybignote on 2009-10-19
as an update - there was a problem with the gnome command, so using the pm-suspend debugging command (had to add to sudoers) allowed mythwelcome to suspend the machine - started up fine .

If anyone knows how to invoke the suspend correctly using hal, that would be better (pm-utils does not recommend running the way I currently have it)

Will test recording schedule now

---

### Post by jonnybignote on 2009-10-19
Machine did not wakeup.  I believe, according to mythbackend.log, the script which translates the utc time, was not allowed to run - the log states that suspend was invoked and then there is no more output.

More investigation needed

Any ideas?

---

