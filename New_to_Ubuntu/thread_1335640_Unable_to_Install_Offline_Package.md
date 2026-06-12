---
title: "Unable to Install Offline Package"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-23
Well, I downloaded virtualbox and when I try to install the .deb, it keeps telling me:

"Only one software management tool is allowed to run at the same time.
Please close the other application e.g. 'Update Manager', 'aptitude', or 'synaptic' first."

I looked at my running processes and I can't find it. Any tips? Also, I was installing it previously and it froze so I had to force close the installer.

---

### Post by Abadon125 on 2009-11-23
When that happened to me the other day I tried restarting the computer.  Try that, if not then try running an update.  I am not the most knowledgeable but when I did it that's what told me there was a problem and how to fix it.

---

### Post by fancypiper on 2009-11-23
# Remove package manager lock
sudo rm /var/lib/dpkg/lock

---

### Post by Buuntu on 2009-11-23
Yeah, like fancypiper said, except the file can be something else.  Usually the error message will tell you what file to remove if you want to disable the lock (ie /var/lib/dpkg/lock).  Always make sure the package management programs/tools are not running first though (if they are, close them :P).

---

### Post by mgranet on 2009-11-23
> **fancypiper said:**
> # Remove package manager lock
sudo rm /var/lib/dpkg/lock

While this does work, it is not a 'best-practice' way of fixing the problem. The lock is there because there could potentially be half-installed software on the system. If you 'break' the lock, and attempt to install the software again, bad things could happen. The best way is to run ```
sudo dpkg --configure -a
```
to allow dpkg to properly address the problem and release the lock.

---

### Post by BT1 on 2009-11-24
Thanks for the assistance. I rounded the cause down to the fact that the installer was hanging (non-responsive) and I had to kill the process which bugged it I guess. I tried the "lock" script and it still had an issue. I since then have uninstalled Ultimate Edition 2.4 because it was just too busy for someone new to linux like me (though it really is pretty nifty). I'm currently restarting my experience in 64 bit Ubuntu 9.10, and installing things as I need them.

I'll keep this tip in mind the next time I run across it.

Thanks!

---

