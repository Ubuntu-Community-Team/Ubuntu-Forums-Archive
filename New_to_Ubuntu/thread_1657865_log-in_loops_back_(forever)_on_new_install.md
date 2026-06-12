---
title: "log-in loops back (forever) on new install"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by pottzie on 2011-01-01
I've just installed Ubuntu 10.01 on an older Dell Optiplex. When the installer gave me the option to boot without having to use a password, I selected that as my preference. Now, after rebooting, all I get is the log-in, and when I enter my password, it loops back into the log-in...over and over.
 This is a computer I'm donating to someone, and for a user AND password, I just went with "myname" for both. Don't know if that's anything to do with the problem. Computer only has 512 ram, but I've had several OS's on it before, without a problem.

---

### Post by sandyd on 2011-01-01
> **pottzie said:**
> I've just installed Ubuntu 10.01 on an older Dell Optiplex. When the installer gave me the option to boot without having to use a password, I selected that as my preference. Now, after rebooting, all I get is the log-in, and when I enter my password, it loops back into the log-in...over and over.
 This is a computer I'm donating to someone, and for a user AND password, I just went with "myname" for both. Don't know if that's anything to do with the problem. Computer only has 512 ram, but I've had several OS's on it before, without a problem.
press control + alt + f1
login.
post output of
cat ~/.xsession-errors

---

### Post by pottzie on 2011-01-01
There may be other "issues." When I installed, I just put the live cd in the tray, booted, and chose "install" without running it. I've just tried to go back and run the cd using the "live" environment, and it's taking forever to load. Maybe there's something screwed up, although I can't imagine what. Hopefully it's just slow because of the low ram, but if it can't load the "live" environment, I'm thinking I've got my work cut out for me. Especially if I'm giving this box to someone who's never used Linux or Ubuntu. I'll try the "cat" if all else fails.

---

