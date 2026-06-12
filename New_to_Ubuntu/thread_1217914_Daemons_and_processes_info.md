---
title: "Daemons and processes info?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by VeskoJl on 2009-07-20
How to find out what's running on my system (not "ps aux" or "top"). For instance I have 2 smbd and 4 windbindd  processes listed in system monitor. Is this correct? Where i can get more info?

---

### Post by toupeiro on 2009-07-20
Well, you just eliminated two very viable ways to find this information out (not ps -aux, or top) and you obviously know about gnome's system monitor?  Do you think one or all of them are lying?

I guess what I am trying to say is, why aren't the daemon and process monitoring tools you are using good enough?

There is always ksysguard (KDE's version of Gnome-system-monitor)  But if you aren't happy with the three you already know about I dont know if its going to be of help to you.

---

### Post by ibutho on 2009-07-20
Well the tools that you have excluded are the ones that can help you. Another good tools are htop, pstree and ksysguard. Some apps may show two or more "processes" because they are multi-threading. For example on my system I have several Apache processes, several postgresql processes and a couple of smbd processes.

---

### Post by VeskoJl on 2009-07-20
Whole confusion comes from that system monitor reports multiple processes with same name and i'm wondering if i messed up the things and installed/configured (if that's possible) 2 samba daemons. Probably ps with other options would give me the answer. :)

---

### Post by mcduck on 2009-07-20
> **VeskoJl said:**
> Whole confusion comes from that system monitor reports multiple processes with same name and i'm wondering if i messed up the things and installed/configured (if that's possible) 2 samba daemons. Probably ps with other options would give me the answer. :)

What you are seeing is the process is running in multiple threads.

At least htop allows you to highlight threads with different color or hide them if you find them annoying.

---

