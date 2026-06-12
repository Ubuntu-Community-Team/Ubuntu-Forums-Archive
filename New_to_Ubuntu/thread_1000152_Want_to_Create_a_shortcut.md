---
title: "Want to Create a shortcut"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by s6pnj on 2008-12-02
Im currently on 8.10 running Gnome and I'd like to create a desktop icon for the following command:

sudo mount 192.168.0.2:/home ~/laptop

When I type this in terminal, it prompts me for my admin password, which I need to input in order to get the sudo mount command to work.  Is there any way I can do this automatically?  I've tried to create a shortcut (right click on the desktop, create Launcher, type - application, command is as per above.

This doesn't work though.  Someone else suggested using connect to server but I can't get anywhere with that as I'm not sure what I type where.  I don't want to auto mount at start-up as the machine I'm 'mounting' won't always be on, so I'd like a desktop icon that I can click rather than typing in a command.

---

### Post by Het Irv on 2008-12-02
Have you tried changing the type to Application in Terminal?

---

### Post by porchrat on 2008-12-02
If something requires root permissions then the only way to stop it requiring "sudo" is to modify sudoers, but I wouldn't recommend that.

---

### Post by kk0sse54 on 2008-12-02
To automount your network drive check out this thread (I assume you are using NFS in this case) [http://ubuntuforums.org/showthread.php?t=646572](http://ubuntuforums.org/showthread.php?t=646572)

---

### Post by Het Irv on 2008-12-02
oh wait, change sudo to gksu, this will give you a graphical prompt.  That may help.

---

