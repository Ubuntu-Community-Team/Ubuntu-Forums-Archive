---
title: "No Password Prompt??"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by waltersfield on 2011-03-06
Just loaded 10.10 alongside of Win.7 on HP G60 laptop. All is well, except for GRUB. I don't get a password prompt. It just automatically logs me in. I set a password during initial setup, and recovery mode asks for my user name and password (which it accepts) so I know it stored it. 

Any suggestions? Thanks!

---

### Post by TeoBigusGeekus on 2011-03-06
You must have checked "log me in automatically" during startup.
It can be changed from admin>System>user accounts (if I remember correctly).

---

### Post by kn0w-b1nary on 2011-03-06
GRUB doesn't automatically log you in, there is a menu option called Login ??? (sorry I can't remeber it at the moment) that you can set to not log you in automatically.

Hope this helps!

---

### Post by mcduck on 2011-03-06
> **waltersfield said:**
> Just loaded 10.10 alongside of Win.7 on HP G60 laptop. All is well, except for GRUB. I don't get a password prompt. It just automatically logs me in. I set a password during initial setup, and recovery mode asks for my user name and password (which it accepts) so I know it stored it. 

Any suggestions? Thanks!

Are you *sure* you are talking about Grub password? Ubuntu's installer doesn't even offer the option of setting up a Grub password...

.. or are you perhaps talking about the actual *login password*? In that case the automatic login can be enabled and disabled in System/Administration/Login Screen.

If you really do mean the Grub password, then here's a guide how to configure that: [http://ubuntuforums.org/showthread.php?t=1369019]("http://ubuntuforums.org/showthread.php?t=1369019")

---

### Post by waltersfield on 2011-03-06
Sorry about the grub term, I say others using it and assumed that was the term for the login prompt.

Anyway, I checked the Sytem/Admin/User Settings and the "don't ask for login password" box is not checked. My Acct. type has me as admin.

---

### Post by mcduck on 2011-03-06
> **waltersfield said:**
> Sorry about the grub term, I say others using it and assumed that was the term for the login prompt.

Anyway, I checked the Sytem/Admin/User Settings and the "don't ask for login password" box is not checked. My Acct. type has me as admin.

Wrong place. ;)

Go to System/Administration/**Login Screen**, like I suggested above, and you'll find an option for disabling automatic login.

---

### Post by waltersfield on 2011-03-06
That did it! Thanks very much for your help!

---

