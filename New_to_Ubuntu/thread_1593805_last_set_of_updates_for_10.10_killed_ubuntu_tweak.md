---
title: "last set of updates for 10.10 killed ubuntu tweak"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-11
did this happen to anyone else

---

### Post by celticbhoy on 2010-10-11
What version of Ubuntu Tweak arfe you using?

---

### Post by rburkartjo on 2010-10-12
celt the newest one since all tweak does now is show the start icon and then quits i dont know for sure but went to tweak website and newest version is 0.5.7.

---

### Post by wilee-nilee on 2010-10-12
Use the ppa.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

Not sure of the problem but you can purge it and reinstall via adding the ppa and key. Mine is running fine in maverick.

---

### Post by rburkartjo on 2010-10-12
wil thanks will try that now

---

### Post by rburkartjo on 2010-10-12
wil did that but it installs ubuntu 5.7.1 and that is where the problem is. that is the one that wont start.

---

### Post by rburkartjo on 2010-10-12
i removed 5.7.1 an installed 5.6.1 same problem. looks like i will have to wait for a fix in the updates/tks

---

### Post by rburkartjo on 2010-10-12
also just used the spm to do a complete removal of ubuntu tweak-that also removes the config files. then re-added the ppa and tried again. same problem

---

### Post by Quackers on 2010-10-12
Does your close button work in a Firefox window?

---

### Post by rburkartjo on 2010-10-13
quack yes

---

### Post by Quackers on 2010-10-13
My FF close problem was fixed with a reboot. I have run ubuntu-tweak since those last updates and it seems to be fine. 
Is it listed as a broken package in Synaptic? (bottom left of the screen)

---

### Post by rburkartjo on 2010-10-13
no quack checked and have no broken packages

---

### Post by rburkartjo on 2010-10-14
i tried to run ubuntu tweak from the terminal
ubuntu-tweak & exit
this normally would run the command and then exit the terminal when i did this got the ubuntu logo screen but then it quit
i received this error when i ran this

ray@ray-desktop:~$ ubuntu-tweak &
[1] 5319
ray@ray-desktop:~$ ERROR:dbus.proxies:Introspect error on :1.57:/com/ubuntu_tweak/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=5319 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=5281 comm="/usr/bin/python))
libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
ray@ray-desktop:~$

---

### Post by rburkartjo on 2010-10-14
okay this is how i fixed. no sure what did it
first opened spm and uninstalled anything with compiz in the name

next went to home opened hiddened folders opened gconf/apps and removed the compiz folder

next opened ubuntu software center and removed anything with compiz in the name

opened the ubuntu software center again and reinstalled anything with compiz in the same with the exception of the one for kde

then click on the desktop change desktop background/visual effects
clicked on extra or custom and it worked. 

desktop effects were enabled as well as ubuntu tweak

---

