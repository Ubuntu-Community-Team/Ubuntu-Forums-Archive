---
title: "unable to shut down using shutdown button"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by KIAaze on 2009-11-05
I'm having a strange problem since today (wasn't there directly after the upgrade to Kubuntu 9.10, but I had some system updates since):
I can't shutdown/restart/logout via the KDE menus (kickoff launcher or application launcher).

The buttons are there and the first time I click on shutdown for example, I do get the shutdown options window, but when I click on shutdown in it, nothing happens.

After the first attempt, clicking on any of the logout/restart/shutdown buttons does nothing at all.

Is this a known bug?

Is there any way to debug those buttons from a terminal?
I couldn't figure out how to launch kickoff from CLI, or find out the command used by the buttons.

Another thing, which might be related or not, is that amarok sometimes fails to start. I have to kill all its process and restart it. + It stopped being able to play any sound files, but can still stream online radio. O.o
(This happened after I tried running it as a startup application with the command "amarok -p SOMEPLAYLIST")

Running kernel version: 2.6.31-14-generic

Don't know if this matters, but I did play with the sudoers file and my current sudoers looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%chvt ALL= NOPASSWD: /usr/bin/chvt

```

edit: Reported as bug: [https://bugs.kde.org/show_bug.cgi?id=213541](https://bugs.kde.org/show_bug.cgi?id=213541)
Problem still not solved.

---

