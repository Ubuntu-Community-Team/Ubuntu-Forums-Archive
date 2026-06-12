---
title: "Wicd problems"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by danip on 2008-04-23
Wicd seems to be the only program that will get my wireless card working but now I cannot get the program to start up.  Here is the output of what happens.

```
steve@weronika:~$ sudo /opt/wicd/gui.py
[sudo] password for steve:
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
steve@weronika:~$ sudo /etc/init.d/wicd start
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 10526
steve@weronika:~$ sudo /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined

```

any help to get this program running again would be much appreciated as I will be in a wireless only area for a few weeks.  thanks!

---

### Post by Whiffle on 2008-04-23
gui.py shouldn't be run with sudo, so try it w/o sudo.

---

### Post by danip on 2008-04-24
```
steve@weronika:~$ /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
```


I tried to do the sudo /etc/init.d/wicd like it says there but this is all that happens:

```
steve@weronika:~$ sudo /etc/init.d/wicd start
[sudo] password for steve:
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 10821

```

---

### Post by Whiffle on 2008-04-24
Looks like the daemon started, what happens if you try /opt/wicd/gui.py again?

---

### Post by danip on 2008-04-24
```
steve@weronika:~$ /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined

```

---

### Post by Whiffle on 2008-04-24
Hmm  very odd.  what if you do 

sudo /opt/wicd/daemon.py

---

### Post by wersdaluv on 2008-04-24
Did you upgrade your distro? Have you tried wireless manager now? If you're willing to run a KDE app, have you tried wlassistant? :)

---

### Post by danip on 2008-04-24
```
steve@weronika:~$ sudo /opt/wicd/daemon.py
/opt/wicd
wicd daemon: pid 11218
steve@weronika:~$ lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.


```

as far as the upgrade I haven't done it yet.  I actually just started runing the update now.

---

### Post by imdano on 2008-04-24
Try deleting /opt/wicd/data/wired-settings.conf, then try starting the daemon again.  Sometimes the conf files get corrupted and cause the daemon to fail to start.

---

### Post by danip on 2008-04-24
Well in combination of deleting that file, running some of the previous commands, and then upgrading the system I got the program to start up and I have my wireless running.  Weird how the network manager wont get it running and only that program will.  Thanks for your help!

---

### Post by jaygo on 2008-05-19
@danip
did you ever get this resolved?

---

### Post by lperez@nmgl.net on 2008-06-19
Hi. I had the same problem... just delete all the *.conf files.
Mine were on /opt/wicd/data...
Then start wicd gui, and all works fine...

---

