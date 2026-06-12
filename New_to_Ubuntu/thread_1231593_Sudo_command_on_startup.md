---
title: "Sudo command on startup"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Buuntu on 2009-08-04
I'm trying to configure my wireless network so it activates on booting up.  Adding ndiswrapper to /etc/modules only causes GNOME to freeze and since I have no idea on how to fix it, I was forced to find another solution.  I soon realized that the network worked after running sudo modprobe ndiswrapper.  So I would like to know if anyone knows of a way to run that command on startup applications or any other way. The reason it won't work under startup applications is that sudo prompts for a password, which I can't enter upon loging in.  I tried adding modprobe and ndiswrapper to sudoers, but that didn't work.  This is what my sudoers file looks like:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias TEST = /sbin/modprobe; /usr/sbin/ndiswrapper

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Defaults:myname timestamp_timeout=1
myname ALL=(ALL) NOPASSWD: TEST
```

---

### Post by bodhi.zazen on 2009-08-04
Try putting your commands, without sudo, into /etc/rc.local (/etc/rc.local runs as root, last, during boot)

---

### Post by Buuntu on 2009-08-04
That worked! Thanks :).  Just out of curiosity, do you know why adding ndiswrapper to /etc/modules would cause the system (or GNOME) to crash?

---

### Post by bodhi.zazen on 2009-08-04
I have no idea =)

My guess is it has to do with the order (during the boot process) of when the modules are added. Adding ndiswrapper into /etc/modules causes ndiswrapper to load before something, most likely networking, is ready.

---

