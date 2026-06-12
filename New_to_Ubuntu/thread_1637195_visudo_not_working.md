---
title: "visudo not working"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by monolux on 2010-12-04
So I've been trying visudo to save my sudoer, because i wanted to remove the sudo password prompt. But it just isn't removing the password prompt for the apt-get. Here is the script:


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset,tty_tickets

# Host alias specification

# User alias specification
 User_Alias MONO =  monolux-S41ILx

# Cmnd alias specification

Cmnd_Alias APT = /usr/bin/apt-get

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
#%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%admin  ALL=(ALL) NOPASSWD: APT

```

And when I run apt-get install something. It still asks for sudo.

```
monolux@monolux-S41ILx:~$ apt-get install fireworks
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
monolux@monolux-S41ILx:~$ 

```

Any help is apreciated. I know I suck :P

---

### Post by CharlesA on 2010-12-04
You need to have the path to the file you don't want to prompt for yer password:

```
/path/to/apt-get
```

---

### Post by monolux on 2010-12-04
Yes that's why APT = /usr/bin/apt-get. Still isn't working.

---

### Post by CharlesA on 2010-12-04
> **monolux said:**
> Yes that's why APT = /usr/bin/apt-get. Still isn't working.

Didn't see that. You still need to use sudo when running a command, it just won't prompt for yer password.

See [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo").

---

