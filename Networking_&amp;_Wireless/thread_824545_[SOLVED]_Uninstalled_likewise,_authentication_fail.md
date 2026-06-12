---
title: "[SOLVED] Uninstalled likewise, authentication failed all the time"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by adwatkin19 on 2008-06-10
I have been testing likewise on my laptop on the work network. I have now just uninstalled it and everytime i try to login i just get the message authentication failed and then returns to the blank username box.

I know that what is going in is correct, but i dont get this. I have tried adding a new user in the command line, same thing happens again, i have tried altering the password, same thing happens again. 

I have autoremoved any packages not needed. Anyone have any ideas?

Thanks alot 

Adam

---

### Post by adwatkin19 on 2008-06-10
I have now fixed this, i realised it was the PAM stuff that was having errors after uninstalling the likewise stuff. So i found a post on these forums that shows how to remove and purge pam and then reinstall

Sorted.

---

### Post by astrotoad on 2008-11-14
I know this thread is stale, but could you post a link to the discussion you are talking about?

The same thing happened to me.  My "solution" was to reinstall likewise.  The uninstallation script does not remove the computer from the domain before uninstalling likewise.

From [this discussion]("https://bugs.launchpad.net/ubuntu/hardy/+source/likewise-open/+bug/230466"):

[INDENT]If you uninstall likewise-open while those system files are still configured to use it (i.e. you're still in the domain), it's like if you uninstalled pam : the system will indeed be mostly unusable. The workaround is the one described by Froza.[/INDENT]

This appear to be a problem with version 4.0.5 (currently in the Hardy repos), and is fixed in 4.1.0.  I wonder if I'll need to upgrade to Intrepid to get the fix.

---

