---
title: "How do I : autostart a program"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by TechDragon on 2010-05-21
I am trying to use a samba share, but apparently it can't survive a reboot I get the following error.

> "net usershare returned error 255: net usershare add: cannot convert name "Everyone" to a SID.  The connection was refused.  Maybe SMBD is not running"

How do I check to see if it running? if not how do I make it autostart?  if it is running what is this error?

Help Please and thank you.

---

### Post by bredman on 2010-05-21
Samba daemon should start automatically, don't try to hack a solution.

Open a terminal (Ctrl-Alt-t) and enter the command
ps -e | grep smb

to see if any samba processes are running.

---

### Post by bredman on 2010-05-21
I forgot to mention that this error message means that samba is not running on the other (remote) machine.

You should enter my command above on the remote machine, not on the local machine.

---

