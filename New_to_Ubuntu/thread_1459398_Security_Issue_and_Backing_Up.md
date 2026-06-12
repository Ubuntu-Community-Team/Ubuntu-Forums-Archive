---
title: "Security Issue and Backing Up"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by sheepdog9090 on 2010-04-21
A complete newbie so here goes:

I left my computer yesterday for an hour and my brother got on it and visited some porn sites. I found out because I caught him. I removed the Flash cookies but am concerned about something being put on the system. I don't have proof just a bit of paranoia.
Needless to say there will be no way for anyone to get on my puter again if I leave the room at all.

The second question is how do I backup files, Firefox Bookmarks, etc using a USB stick? Is there a way to set it up daily?

Thanks for any help.

---

### Post by natravis on 2010-04-21
Backup: read through this link and if you don't find a solution or have questions, try checking the program's site, then ask here 
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Security: it is doubtful that there is anything on your system but there are rootkit checkers out there. The anti-virus clients available for Ubuntu would not be useful to you because they are essentially checks for viruses that will affect windows clients. Be aware that it is quite hard to compromise Ubuntu, but feel free to peruse the security forums.

---

### Post by ed-koala on 2010-04-21
If you dual boot Windows you might have a problem as a Windows virus might have gotten in.  It won't hurt Ubuntu though.

---

### Post by sheepdog9090 on 2010-04-21
> Backup: read through this link and if you don't find a solution or have questions, try checking the program's site, then ask here 
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I will read it. Is it the same for a USB stick as a LiveCD?


> If you dual boot Windows you might have a problem as a Windows virus might have gotten in.  It won't hurt Ubuntu though.


No, I am running Ubuntu solely. No more windows.
[]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by natravis on 2010-04-21
Are you running Ubuntu from a USB stick? Backing up should still be similar to a normal install but would be different than a LiveCD. Anything you "installed" on a LiveCD would be gone, so you'd have to reinstall and configure the backup software each time you rebooted. If it is possible, install Ubuntu on your computers HDD and backup to the USB drive.

---

### Post by sheepdog9090 on 2010-04-21
> Are you running Ubuntu from a USB stick? 

No. I can't burn CD's so my option is to backup to a stick.

---

### Post by sheepdog9090 on 2010-04-21
> install Ubuntu on your computers HDD and backup to the USB drive.

It is on my HDD. My question is how to back up to the USB drive?

---

### Post by lovinglinux on 2010-04-21
Use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) to backup your profile daily or when the browser starts or when the browser closes.

Use [Public Fox](https://addons.mozilla.org/en-US/firefox/addon/3911) to limit what your brother can do with Firefox.

Use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) for security.

See more security extensions [here](https://addons.mozilla.org/en-US/firefox/collection/securityandprivacy).

---

### Post by sheepdog9090 on 2010-04-22
Thank you!

---

### Post by RedRat on 2010-04-22
> **lovinglinux said:**
> Use [FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") to backup your profile daily or when the browser starts or when the browser closes.

Use [Public Fox]("https://addons.mozilla.org/en-US/firefox/addon/3911") to limit what your brother can do with Firefox.

Use [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") for security.

See more security extensions [here]("https://addons.mozilla.org/en-US/firefox/collection/securityandprivacy").

The problem with NoScript is that once your brother is in FireFox he can easily go to the NoScript right-click menu and open all the scripts on a given page. At the end, you must realize that you have a nosy brother who has some computer skills so you must password protect your computer, perhaps through a screensaver login.

---

### Post by -humanaut- on 2010-04-22
One thing that i've done to back up files is I Created a 3GB Fat32 Filesystem on my harddrive that I keep unmounted at all times with all my important files and settings on.

---

### Post by Drenriza on 2010-04-22
for backup look here
_[COLOR=#800080][http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)[/COLOR]_
_[COLOR=#800080][/COLOR]_ 
_[COLOR=#800080][/COLOR]_[]("http://ubuntuforums.org/forumdisplay.php?f=100")

---

