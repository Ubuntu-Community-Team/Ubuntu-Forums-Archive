---
title: "/etc/sudoers file"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by donaldshelton on 2010-01-01
I tried to follow directions posted by a user that would have eliminated the need to enter a password after the sudo command.

The result is that I get an error message whenever I try to do administrative commands with the terminal.  Also, none of the administrative applications will open.

Can someone help me get it back to the way it used to be?[IMG]http://img222.imageshack.us/img222/2230/screenshottnv.png[/IMG]

---

### Post by mkoehler on 2010-01-01
If you just use gksudo and work backwards through all of the commands that you did, then you should be able to get everything back to a working condition.

---

### Post by jbrown96 on 2010-01-01
Do not edit /etc/sudoers!!!! 

You must use ```
sudo visudo
``` because it will check to make sure you don't make any errors before you exit. If you save and exit that file with errors, you can make it impossible to do any administrative task.

1) Fix the permissions ```
sudo chmod 440 /etc/sudoers
```
If that doesn't work, then you will need to boot from a live cd and do all these instructions from the live cd.

2) Restore /etc/sudoers. Here is my file > # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%admin ALL=NOPASSWD: /usr/sbin/powertop
%admin ALL=NOPASSWD: /usr/bin/apt-get update
%admin ALL=NOPASSWD: /usr/bin/apt-get upgrade
%admin ALL=NOPASSWD: /usr/sbin/pm-suspend
%admin ALL=NOPASSWD: /sbin/reboot
%admin ALL=NOPASSWD: /sbin/fdisk -l

Those last six lines are my modifications, so you might not want to include them. Just copy and paste all of it, except the last six lines. I left them in there, so you would know the format of the entries that you want to make -- so you can execute commands w/o a password.

Remember, use ```
sudo visudo
```

---

### Post by Najand on 2010-01-01
If vi(m) is difficult for you to use, you can use
```

sudoedit /etc/sudoers

```

It uses the default editor which I believed is set to nano by default which is easier to use than vi(m) for beginers.

---

### Post by jbrown96 on 2010-01-02
> **Najand said:**
> If vi(m) is difficult for you to use, you can use
```

sudoedit /etc/sudoers

```

It uses the default editor which I believed is set to nano by default which is easier to use than vi(m) for beginers.

In 9.10, it sudo visudo automatically uses the default editor, which is nano. No need to use a separate command.

---

