---
title: "Lucid won't shutdown (sudoers?)"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-07-14
Gurus,

I have a 32 bits desktop install of Lucid 10.04.

To save $$$ on my power bill, I want to shutdown my machine every night at 10PM. So I created a CRON job 

```
00 22 * * * /usr/sbin/sudo /sbin/shutdown -h now
```It does not work. I found no errors (permissions?) in the log file... the machine never shuts down. However, if I do exactly the same thing from the command line, it works!!

After doing some research, I edited my sudoers file thusly
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
Cmnd_Alias USR_CMDS = /sbin/shutdown

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# User Alias specification
User_Alias USERS = alberto

# User alias specification
ALL ALL=(ALL) NOPASSWD: USR_CMDS

```No change. The CRON job does not work, however the command line works just fine.

What am I missing here? Can someone help? Thank you.

Al.

---

### Post by TechBeastie on 2010-07-14
You might try putting the entire command sequence into a separate script, and then getting that script to work outside of cron.  (IE, make a separate file, consisting of the following: ```

#! /bin/sh
sudo shutdown -h now

```
and then try manually running it from the command line.  If it works, try having cron run that script directly, instead of the compound command).  

Also, I don't think you need either the command alias or the user alias, although I can't see why having them in would hurt either (assuming you've gotten the syntax right).  The only line you should really need is:
```
 ALL ALL=(ALL) NOPASSWD: /sbin/shutdown 
```

---

### Post by JKyleOKC on 2010-07-15
Cron jobs run as root and so do not need "sudo" as the start of the command. Try it with just "shutdown -h now" and see if that does not work as intended.

---

### Post by kristo5747 on 2010-07-15
> **TechBeastie said:**
> You might try putting the entire command sequence into a separate script, and then getting that script to work outside of cron.  (IE, make a separate file, consisting of the following: ```

#! /bin/sh
sudo shutdown -h now

```and then try manually running it from the command line.  If it works, try having cron run that script directly, instead of the compound command).  

Also, I don't think you need either the command alias or the user alias, although I can't see why having them in would hurt either (assuming you've gotten the syntax right).  The only line you should really need is:
```
 ALL ALL=(ALL) NOPASSWD: /sbin/shutdown 
```

Did exactly what you suggested 

a) created a small script and put it in CRON (instead of what I initially did)
2) removed the command alias in my /etc/sudoers.

...and...

IT WORKED!!! 

Thanks, Man! =D>

---

