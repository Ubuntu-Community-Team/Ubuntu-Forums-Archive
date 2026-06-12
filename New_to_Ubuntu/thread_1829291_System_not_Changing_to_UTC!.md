---
title: "System not Changing to UTC!"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by NCMS on 2011-08-20
I am running 10.04.3 LTS,  I have changed the UTC to yes  in the file  **/etc/default/rcS**  and rebooted the system but it is still shown time in LOCAL TIME  ...
[B]
am I missing anything ?

[SIZE=3]cat /etc/default/rcS[/SIZE][/B][SIZE=3]
[/SIZE]#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
[B][COLOR=Red]UTC=yes
[/COLOR][/B]VERBOSE=no
FSCKFIX=no
ncms@ncms-laptop:~$

---

### Post by Cheesehead on 2011-08-20
UTC=yes should already be set by default.
Your system should already be keeping UTC plus your local timezone.

Command line ways to check and change time (see [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) )
```

date -u              # Check UTC
date                 # Check local time
sudo dpkg-reconfigure tzdata     # Change the local time by changing time zone
```

---

### Post by NCMS on 2011-08-21
Thanks, you are right and time settings are fine, actually I meant the time displayed on the PANEL is local time, and I don't know how to change it to UTC  

In RedHat  I was able to do it by selecting UTC from the Preferences ..

Is it possible ?

---

### Post by NCMS on 2011-08-23
I found the solution in this URL  
[COLOR=Red][B][http://askubuntu.com/questions/6928/is-there-any-way-to-display-time-in-utc-on-the-panel](http://askubuntu.com/questions/6928/is-there-any-way-to-display-time-in-utc-on-the-panel)
[/B][/COLOR]
thanks to [andrewsomething]("http://askubuntu.com/users/570/andrewsomething")

---

