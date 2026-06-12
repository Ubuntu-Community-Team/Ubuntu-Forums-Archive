---
title: "Restarting /etc/init.d scripts as regular user?"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by flywheelbot on 2007-04-05
I'd like to be able to restart dbus on my Ubuntu 6.10 box (as well as other services, like vmware, samba).

But with recent security changes at my workplace, I won't be able to use either su or sudo to accomplish this.

Does anyone know how to allow a regular user to run /etc/init.d/ scripts without manually changing the ownership of all the directories, scripts, and executables they run?  (ie, limited chmod u+s).  It's tricky without using sudo or su.

Perhaps it could be done through pam, or by creating a user with a shell that executes only that command?  I'd like to do this as cleanly as possible, given the circumstances.

Thanks for the help,
flywheelbot

---

### Post by flywheelbot on 2007-04-05
I should add that the reason for wanting to restart /etc/init.d is primarily to get NetworkManager restarted (for a wireless card)--hence why I picked this topic.

-flywheelbot

---

