---
title: "User-friendly backup program"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by cpeachey on 2009-07-07
I have Jaunty 9.04 (AMD64) and want to backup to a USB hard drive, preferably automatically, once a day whenever the computer is switched on.
I have tried "SimpleBackup" and a couple of others but without success. One problem was ......"***.pl command not found"
Any tips please? My use of "Terminal" is limited to copying instructions from elsewhere. (I don't do programming!)
Chris

---

### Post by aysiu on 2009-07-07
How about Grsync? I think that's in the repositories. It's a graphical frontend for *rsync*, which backs up only changed or added files since the last backup.

---

### Post by scrooge_74 on 2009-07-07
Works pretty well I may add

---

### Post by cpeachey on 2009-07-07
I'll try that tomorrow. I do not have any backup at the moment. Is there anything obvious that would stop the *.pl command from working?.. like an extra utility I should have installed?
Chris

---

### Post by cpeachey on 2009-07-07
Just tried grsync. Easy to use and understand. Got a message..
rsync: opendir "/home/chris/.sane/xsane/batch-lists" failed: Permission denied (13)
I am not quite sure how critical this is. (I am the sole user of this pc):
Thanks for your response. Any other backup tips etc most welcome.
Chris:p

---

### Post by RJARRRPCGP on 2009-07-07
You must use ```
sudo
``` and try again.

---

### Post by aysiu on 2009-07-07
You should own everything in your home directory. Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
sudo chown -R chris:chris /home/chris
``` and try Grsync again.

Grsync should not have to be run as root (and if it were to be run as root, it should be with *gksudo/I] and not [I]sudo*).

---

