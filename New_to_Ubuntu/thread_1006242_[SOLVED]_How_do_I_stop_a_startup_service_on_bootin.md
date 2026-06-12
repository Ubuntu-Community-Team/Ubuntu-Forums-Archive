---
title: "[SOLVED] How do I stop a startup service on booting?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by eber69 on 2008-12-09
Hi,
I'm running 8.04 Ubuntu and have installed Freevo for TV use. On installation I choose to automatically start the Freevo server. I regret this and want to undo it. Hence, how can I stop a startup service when booting and make it permanently not run on boot up?
Cheers

---

### Post by davidbilla on 2008-12-09
Try,

System -> Administration -> Services, if it's a daemon.

Or, try,

System->Preferences->Sessions->Startup Programs.

---

### Post by stevoo on 2008-12-09
check in the 
System-> Preferences -> Sessions.

Most probably the application will be in there. If it is un tick  and that is it :) 

if not let us know !

---

### Post by eber69 on 2008-12-09
> **davidbilla said:**
> Try,

System -> Administration -> Services, if it's a daemon.

Or, try,

System->Preferences->Sessions->Startup Programs.

Right, the problem is I can't reach the GUI. I have to use the console, since Freevo won't let me get to the KDE(?) GUI.

---

### Post by catcharavind2003 on 2008-12-09
With the latest packages in Debian 4.1, most freevo-related services are started by default. To change the default settings, run `dpkg-reconfigure -p low freevo'.

---

### Post by stevoo on 2008-12-09
so we can kill freedo and try again

try 
ps -A | grep freedo 
see if we can find the process there
if yes
run : kill <process number of freedo here>
and try again !

---

### Post by eldragon on 2008-12-09
```

$ cd ~/.config/autostart
$ ls

```

you will see all apps being run with your session there.....to disable. just remove the executable flag

```

$ chmod -x the_nasty_app.desktop

```

restart X

---

### Post by wizard10000 on 2008-12-09
The services applet is IMO of limited use.  I suggest using Boot Up Manager

sudo apt-get install bum

or if you want an excellent but slightly intimidating tool -

sudo sysv-rc-conf

which is a runlevel editor and extremely powerful - but also exceedingly dangerous if you're not paying attention.

Good luck -

---

### Post by oldos2er on 2008-12-09
+1 for sysv-rc-conf.

---

### Post by eber69 on 2008-12-10
Thanks a bunch, guys. You are great!!!!

---

