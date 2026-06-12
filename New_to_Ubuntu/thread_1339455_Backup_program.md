---
title: "Backup program"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Kjasontu on 2009-11-27
I can't seem to find a program that will let me schedule a backup to an external drive of my /home directory.  Does anyone know of any software?

---

### Post by Arla on 2009-11-27
This thread

[http://ubuntuforums.org/showthread.php?t=592445](http://ubuntuforums.org/showthread.php?t=592445)

Has some information on scheduled backups

You could probably also use Gnome-Schedule and the TAR command (I'm guessing here, not done it myself).

---

### Post by Temposs on 2009-11-27
A great backup program that I use and contribute to is called Deja Dup. It's in the repositories(Add/Remove, Ubuntu Software Center), so look it up. It's really easy to use.

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by Kjasontu on 2009-11-27
Thanks!  I will give it a shot.

---

### Post by XCan on 2009-11-28
I would say rsync, but perhaps cli is not preferred? 
```
 rsync -avz --delete /home/user /path/to/external/drive 
``` is all that's needed to be added in crontab. :)

---

### Post by stinkeye on 2009-11-29
There is grsync a gui for rsync.

or the easiest way not using the command line that I know is by 
installing [_[COLOR="DarkRed"]QuickStart: Download & Pics[/COLOR]_]("http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html")
and it wil run you through a series of pop-up windows.

---

### Post by stinkeye on 2009-11-29
> **Temposs said:**
> A great backup program that I use and contribute to is called Deja Dup. It's in the repositories(Add/Remove, Ubuntu Software Center), so look it up. It's really easy to use.

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)
Just tried it.Very good.Nice and simple to use.
Also allows to exclude folders which quickstart doesn't.
Think I'll switch. :D

---

### Post by Magical Tiger on 2009-11-29
There is SBackup. Its in the repos and has scheduled backups and support for logarithmic deletion (keeping some old backups, but not all) and many other things. It also has a very easy gui and I have seen many recommendations for it so you should give it a try.

---

