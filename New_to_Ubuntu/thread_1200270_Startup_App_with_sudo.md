---
title: "Startup App with sudo"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by gurt on 2009-06-29
I have an application that I want to Startup automatically every time. But the application requires sudo and a password. How can I automate starting up this app?

bam@mingus:/opt/dynamips$ sudo dynamips -H 7200
[sudo] password for bam:

Ta!

---

### Post by ~sHyLoCk~ on 2009-06-29
```
sudo visudo
```

And add this:~ 
```
bam ALL = NOPASSWD: /opt/dynamips/dynamips
```

Create an entry in your Preferences->Startup Applications and put this:
```
dynamips -H 7200 
```
Reboot and see if it works?

---

### Post by gurt on 2009-06-30
Thanks for the reply!
It doesn't seem to be working. I see the dynamips process in the System Manager. But the app that uses Dynamips (cllaed Dynagen) just hangs. If I edn the dynamips process and relaunch it manually 'sudo dynamips -H 7200', then dynagen works OK.

Any ideas on how to troubleshoot this?

Thanks for turning me onto visudo! :cool:

---

### Post by Thingymebob on 2009-06-30
edit /etc/rc.local
and add dynamips -H 7200
before the exit 0 statement

---

### Post by gurt on 2009-06-30
That worked Thingymebob -- Thanks!

I noticed that the dynamips process isn't showing up in the System Monitor/Processes. How's that?

---

### Post by Thingymebob on 2009-06-30
I think, but am happy to be corrected here, its because system monitor only shows processes owned by the user, and your dynamips process is owned by root. You can confirm this behaviour by creating a process as yourself, e.g just enter top in a terminal and the process will appear in system monitor. However if you enter sudo top, the process will not appear.

---

