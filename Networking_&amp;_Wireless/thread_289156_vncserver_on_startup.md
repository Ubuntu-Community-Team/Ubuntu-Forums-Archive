---
title: "vncserver on startup"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2006-10-30
Hi - I've installed vncserver and got it up and running.  I'm able to logon to it from my Windows XP machine.  However, I want to be able to have it start up a session when the Ubuntu machine boots up.  I have tried putting in the following code into the /etc/rc.local file

```
/etc/init.d/vncserver start
```

and

```
vncserver -geometry 1024x768 -depth 16 :1
```

However, if I go to the monitor and type in the vncserver command line after reboot, it works fine.  What am I doing wrong?  I also tried putting in a password for both su and myself - was that a mistake?

---

