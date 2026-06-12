---
title: "Send commands to windows from ubuntu"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by Fir3chi3f on 2008-11-30
Sounds simple and probably is but, does anyone know how to send (windows) commands to a windows box from Ubuntu?

---

### Post by cmnorton on 2008-11-30
Do you mean log in and enter some commands, or do you want to "send over" a batch file containing one or more commands to be executed? The only thing I can think of is have an ssh server running on the Windows box. There are more sophisticated ways to handle this with network programming, but it does not sound as if that is what you want.

---

### Post by Fir3chi3f on 2008-11-30
Login and enter some commands.

Thanks for the clarification, any suggestions? 
Preferably without installing anything on the windows machine.

---

### Post by damis648 on 2008-11-30
You will be probably wanting [this]("http://sshwindows.sourceforge.net/") or [this]("http://www.kpym.com/2/kpym/index.htm"), it is an SSH server for Windows, I do not think there are many options for without installing anything on the Windows machine. Anyway, both links seem to be good options. Check them out. One is just an SSH server, the other SSH and Telnet.

---

