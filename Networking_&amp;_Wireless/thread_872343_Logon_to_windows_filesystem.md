---
title: "Logon to windows filesystem"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Hans5849 on 2008-07-27
Before I upgraded I could Samba into my XP machine and I would logon using my XP username and pass. It would display not just my windows shares but the entire disk directory on my XP machine. Basically I was remote desktopping into the file system of my xp machine before using samba and now I can't.

These are the changes I've made since Ubuntu > Hardy XP SP2 > XP SP3

---

### Post by sdowney717 on 2008-07-27
well try this
share a folder on XP machine
click places - connect to server

select service type windows share

under server, enter the IP address of the XP machine

click connect, it will ask you for password, put in your ubuntu password.
You should now see you XP shares listed in the file manager.

---

### Post by Hans5849 on 2008-07-29
The only thing is I am not looking for the shares, I am looking to log onto the file system. Before when I did it I could login and get my C:\ that wasn't shared.

---

### Post by cariboo on 2008-07-30
Looks like sp3 closed a big security hole in your system.

JIm

---

