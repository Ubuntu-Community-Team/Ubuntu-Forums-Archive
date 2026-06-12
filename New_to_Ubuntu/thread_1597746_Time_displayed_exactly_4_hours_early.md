---
title: "Time displayed exactly 4 hours early"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by MikeB23930 on 2010-10-15
I'm running Xubuntu 10.10.  The time displayed in the panel with either Orage or Clock is exactly 4 hours earlier than the actual local time.  I have reconfigured tzdata several times and I have tried both UTC=yes and UTC=no in /etc/default/rcS.

In case it helps, here is a typical output from running 
dpkg-reconfigure tzdata:

Current default time zone: 'America/New_York'
Local time is now:      Fri Oct 15 12:28:53 EDT 2010.
Universal Time is now:  Fri Oct 15 16:28:53 UTC 2010.

The time zone is correct but what is reported as the Universal Time is what should be displayed in the panel as the local time.

Can someone please tell me how to correct this situation?

Thanks,

Mike

---

### Post by Sealbhach on 2010-10-15
Maybe just change your location in the panel applet as well. Just right-click and preferences.

.

---

### Post by Frogs Hair on 2010-10-15
Did you select the proper time zone on the where are page during the installation ?

---

### Post by MikeB23930 on 2010-10-15
There was a setting for the time zone in the properties popup for orage and that did the trick.  Simple.
  
Thanks, Sealbhach.

Mike

---

