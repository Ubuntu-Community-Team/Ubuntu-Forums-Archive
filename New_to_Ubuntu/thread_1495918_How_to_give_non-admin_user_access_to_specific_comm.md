---
title: "How to give non-admin user access to specific commands"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by hogarth on 2010-05-28
Hi all,

So i'm dabbling with admin stuff and don't know much about anything... long story short i have two users on my computer (running Ubuntu Server 8.04, for the record): one is 'sysadmin' with full privileges and all, and the other is 'newuser', who does not have admin privileges.

What i want is to give 'newuser' the ability to do some basic commands, such as:
sudo aptitude update && sudo aptitude safe-upgrade
shutdown -r now
etc...

I've heard that i have to edit the /etc/sudoers file (which i guess i would do with the 'sysadmin' account). But i only want to give 'newuser' access to those specific commands (otherwise it defies the whole point of 'newuser' not being an admin user).

Does anyone know how i could do that?

Thanks!

---

### Post by anantshri on 2010-05-28
these two threads might help

[http://www.linuxquestions.org/questions/slackware-14/sudoers-specific-permission-741026/](http://www.linuxquestions.org/questions/slackware-14/sudoers-specific-permission-741026/)

[http://ubuntuforums.org/showthread.php?t=680800](http://ubuntuforums.org/showthread.php?t=680800)

---

### Post by hogarth on 2010-05-30
> **anantshri said:**
> these two threads might help

[http://www.linuxquestions.org/questions/slackware-14/sudoers-specific-permission-741026/](http://www.linuxquestions.org/questions/slackware-14/sudoers-specific-permission-741026/)

[http://ubuntuforums.org/showthread.php?t=680800](http://ubuntuforums.org/showthread.php?t=680800)

Thanks, i looked em over ... but i still don't think that will quite cut it.

WARNING: this could be that i don't have the necessary understanding of how it all works, so feel free to rebuke me if i'm screwing up. That said, i want (e.g.) 'newuser' to be able to run "SUDO aptitude update" (among others). That is, i want "him" (without loss of generality, you may assume i said "her" :) ) to have to still be prompted for his password in order to perform updates. So i don't want to completely disable the password requirement for that command.

So i guess i'm asking if it's possible to give someone w/o admin status the ability to run a specific "sudo" command (by editing /etc/sudoers appropriately)?? I thought that you would be prompted for your own password when using sudo (provided you weren't trying to do some mega-privileged command)...

Sorry in advance for my confusion...

---

### Post by nhasian on 2010-05-30
Yes, take a look at:

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

under the title "Restricting Application Usage"

> **hogarth said:**
> So i guess i'm asking if it's possible to give someone w/o admin status the ability to run a specific "sudo" command (by editing /etc/sudoers appropriately)?? I thought that you would be prompted for your own password when using sudo (provided you weren't trying to do some mega-privileged command)...


---

### Post by hogarth on 2010-05-30
> **nhasian said:**
> Yes, take a look at:

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

under the title "Restricting Application Usage"

Alright thanks, that helped a lot!

When i go back to my ubuntu comp on Tuesday i'll post some code of what i do specifically (in the 'sudoers' file)... just in case anyone out there is as daft as i am when it comes to this stuff and needs to see yet another example.

Thanks all

---

### Post by hogarth on 2010-06-01
Okay, for all who need it spelled out exactly (as i do), here's the line i added to the 'sudoers' file:

```
newuser comp=(ALL) /usr/bin/aptitude update,/usr/bin/aptitude safe-upgrade
```

This will give the user 'newuser' on the computer called 'comp' access to the update and safe-upgrade commands, while still prompting him for his password. I'm thrilled.

---

