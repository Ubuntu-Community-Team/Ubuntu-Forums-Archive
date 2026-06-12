---
title: "visudo not working?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by glisignoli on 2010-08-13
Hello!
I followed the tutorial [here](https://help.ubuntu.com/community/Sudoers) but it doesn't seem to work :(

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
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown/, /sbin/halt/, /sbin/restart
# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
networkserver ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

```

```

networkserver@networkServer:~$ shutdown now -r
shutdown: Need to be root

```

I've tried restarting (as sudo) logging back on as "networkserver" but the changes don't seem to have made any difference. Any clues?

---

### Post by glisignoli on 2010-08-13
I'm a noob....

sudo shutdown now -r works....

---

