---
title: "Remote desktop in Ubuntu - why is it painfull to use?"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by petegregar on 2013-11-16
I have a main PC in my basement that acts like a server.
Lots of file storage, that I stream to other equipment in the house.
It is on ethernet to the wireless router.

Machine used to be Win7
My laptops used to be Win 7
Remote Desktop worked great.  It was like I was sitting in the basement on the machine.

NOW
All machines are Ubuntu 13.10
All machines communicate over network fine.
Remote desktop is terrible.

The screen does not fit my laptop size, I have to scroll around
Had to disconnect the dual monitor, cause that would not allow the remote to work.
Laggy and stutters.

Any suggestions?  Do I need something dedicated intstalled on each machine to make this work better?

---

### Post by QIII on 2013-11-16
I use NoMachine NX to remote to my other Linux machines.  It's a bit of a pain to set up the first time you try, but NX is a lot more efficient and blows VNC and the like out of the water with regard to performance.  Audio from the server to the client is problematic to the point of non-existent, though.

---

### Post by petegregar on 2013-11-16
I will try that.
Audio is not an issue.
I just remote in to manage files and back-up new items.

---

### Post by houstonbofh on 2013-11-16
You might consider things like "ssh -X" and Gnome's built in "Connect to server" over ssh.  Sometimes a full remote desktop is not the best way to move information.

---

