---
title: "Corrupted 8.10 - Will distro upgrade to 9.04 clear it?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by resander on 2010-04-27
I am the one recently posting 'How to cancel 409 pending updates?'.  That question is not relevant any more. The problem is more serious. I caused it by requesting a repository for a 
more recent version (10.04?) and responding to the update notification.

Result: 8.10 is corrupted.

I cannot login from the login dialog. The cursor/caret sits there blinking, but it does not accept any keyboard input. I can log in on the command line after Alt+F1. All the important files and directories are intact, but GUI functions like gedit and brasero produce error message: 

GTK-warning: ** cannot open Display.

Q1.
Will 'sudo do-release-upgrade' (to 9.04?) from the commandline clear the problem or could it make it worse? Does do-release-upgrade need any parameters? 

Q2.
Are there other ways to solve this?

---

### Post by QLee on 2010-04-27
> **resander said:**
> I am the one recently posting 'How to cancel 409 pending updates?'.
Q1.
Will 'sudo do-release-upgrade' (to 9.04?) from the commandline clear the problem or could it make it worse? Does do-release-upgrade need any parameters? 

Not likely to clear the problem.

Edit: If you do choose to try it, make it a "last resort" Another option might be upgrade to 10.04, might work, might not another "last resort" But if your system is one that would be affected by one of the current bugs, upgrading to it might just introduce new problems.

[QUOTE=resander]Q2.
Are there other ways to solve this?[/QUOTE]

Still the same as I gave in your other thread.
[http://ubuntuforums.org/showthread.php?p=9180869#post9180869](http://ubuntuforums.org/showthread.php?p=9180869#post9180869)

I wish I had better news for you!

Edit: Be sure to tell everything you did when asking for help, the fact that you used Debian,Squeeze repository can be an important distinction from 10.04 which you cited here. I only knew from the other thread.

---

### Post by egalvan on 2010-04-27
> **resander said:**
> 'How to cancel 409 pending updates?'.
 The problem is more serious. 
Are there other ways to solve this?

Ubuntu Help states an up-do-date system (all updates installed) as a requirement for an up-grade to 10.04.

so if you indeed canceled 409 pending updates, then the up-grade will not be successful, and you will probably experience further problems.

Personally, I would back up needed data, wipe 8.10. and do a clean 10.04 install.

My two work machines, running 8.04, will go that route.
Clean start.

---

