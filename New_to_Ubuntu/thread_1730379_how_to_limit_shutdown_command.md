---
title: "how to limit shutdown command"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by node2network on 2011-04-16
The [question]("http://ubuntuforums.org/showthread.php?t=1729728") which I asked in this forums before were solved, but I don't know how to limit shutdown command on gnome-terminal.
I don't want to let users(is added admin group) use the shutdown command only during backup.
I know how to limit shutdown commands permanently.

# sudo VISUAL=vim visudo

edit /etc/suders

Cmnd_Alias SHUTDOWN = /sbin/halt, /sbin/shutdown, \
/sbin/poweroff, /sbin/reboot, /sbin/fastboot, /sbin/init

%hogehoge ALL=(ALL) ALL,!SHUTDOWN

I want to know how to limit shutdown commands only during backup.

---

### Post by rosencrantz on 2011-04-16
OK, bit of an ugly hack...
How about writing a script that first disables shutdown rights by changing the /etc/sudoers file, then runs the backup and changes everything back afterwards? Keep 2 backup versions of /etc/sudoers, a normal and a restricted one, and have them copied to the active file.
Execute with sudo:
```
#!/bin/bash 
cp /etc/sudoers.restricted /etc/sudoers
#do some backup magic
cp /etc/sudoers.normal /etc/sudoers
```
Have a backup copy of the normal /etc/sudoers in a safe place, just to make sure.

---

### Post by node2network on 2011-04-16
thank you for your reply.

I try this.
For example, when I try to shutdown, gnome-terminal shows 
"Sorry, user foofoo is not allowed to execute '/sbin/shutdown -h now' as root on ssh-server".

Furthermore, I want to display 
"Sorry, user foofoo is not allowed to execute '/sbin/shutdown -h now' as root on ssh-server during backup. Please try again later".

Can  I  do this?

---

### Post by rosencrantz on 2011-04-16
Hm. Another ugly hack coming ;-)
In that case, editing sudoers is not going to help. You could try 
temporarily rerouting /sbin/shutdown
Again, make an additional backup of /sbin/shutdown before you do this. If you corrupt the file, you are in big trouble.
Copy this as noshutdown to /usr/bin and make it executable.
```

#!/bin/bash
zenity --text 'Please come back later.' --info
```


```

#!/bin/bash
cp /sbin/shutdown /sbin/shutdown.old
ln -s /usr/bin/noshutdown /sbin/shutdown
#do backup
cp /sbin/shutdown.old /sbin/shutdown

```

I haven't time to try this in detail, as I'm off to the opera right now. I'll get back to this thread in a few hours.

---

### Post by rosencrantz on 2011-04-16
OK, it doesn't quite work as expected, renaming shutdown makes the user log out instead of shutting down and displays no message. I suppose that's pretty much what the sudoers hack does, too.
I suppose logging out of a user session is something that has to be always allowed. If it's handled by a script, it would be easy to sneak in the zenity box somwhere, but at the moment I have no clue which apps and scripts are called during logout and shutdown.

---

