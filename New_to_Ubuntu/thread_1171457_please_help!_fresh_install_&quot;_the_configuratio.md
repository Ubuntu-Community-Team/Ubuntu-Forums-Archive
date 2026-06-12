---
title: "please help! fresh install: &quot; the configuration could not be loaded&quot; no sudo rights"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by new_user_ny on 2009-05-27
this might be a stupid question or a bug:
i just installed ubuntu 9.04 and have no sudo rights.
i tried to go to system-administration-users & groups, i was hoping to get an UNLOCK option.
However, i get the following message: 
"the configuration could not be loaded"
followed by: "you are not allowed to access the system configuration".

needless to say, i have no sudo rights. 
i have only 1 account set up on the system (that i set up on install) and when i try a sudo command it says i don't have privileges to do so.

any idea?

thanks for the help.

---

### Post by mapes12 on 2009-05-27
How did you install?

Ubu only on the PC?

Dual boot?

Within Widows e.g. wubi etc.?

How did you set up your partitions?

---

### Post by new_user_ny on 2009-05-27
i installed on a PS3. following the best practices on the web.
basically, formated the PS3, created a new partition, rebooted of the 9.04 ISO CD for PS3, went through the install process (which was simple and solid) and here i am...

during the install process i was prompted to set up a user/password. these work, and allow me to login to the desktop, but i can't do much when i'm there.

thanks for the help!!

---

### Post by sisco311 on 2009-05-27
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by new_user_ny on 2009-05-27
thanks - looks like a good site. and on the right track.
stupid question - how do i enter recovery mode when using kboot and not grub?

i tried going into sh (which i assume is shell) but i don't know which commands to enter, as the ones mentioned in the link above aren't working (n/ etc/ not found)

thanks agian

---

### Post by laughing_badger on 2009-05-28
Just posting to confirm the above problem with a default install of 9.04 on PS3 using the alternate installer disk. I'll also try the above link for a fix when I get home.

---

### Post by sisco311 on 2009-05-28
> **new_user_ny said:**
> 
stupid question - how do i enter recovery mode when using kboot and not grub?

thanks agian

[list=i]
[*]at the kboot prompt type *sh* to start a shell.



[*]remount the root partition:
```
umount /mnt/root
mount -t ext3 -w /dev/ps3da1 /mnt/root
```



[*]chroot into the root partition:
```
chroot /mnt/root bash
```



[*]add your user to the admin group:
```
adduser username admin
```



[*]backup and edit the sudoers file (if needed):
```
cp /etc/sudoers /etc/sudoers.backup
EDITOR=nano visudo
```


the default file looks like this:
```
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
**root	ALL=(ALL) ALL**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**
```

When you are done, press: Ctrl+x, y, Enter (save the file and exit)



[*]make sure the file has the correct permissions:
```
chmod 0440 /etc/sudoers
```



[*]press Ctrl+d to exit from the chroot or type:
```
exit
```



[*]repeat the previous step to exit from the BusyBox shell.



[*]at the kboot prompt boot the system in the normal way.

[/list]

---

### Post by laughing_badger on 2009-05-28
Thanks sisko311!

Up and working.

---

