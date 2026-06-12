---
title: "Ubuntu Jaunty file and public folder sharing tutorial by Powel212"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by powel212 on 2009-08-06
Ubuntu Jaunty file and public folder sharing tutorial by Powel212

This is a tutorial on how to properly set up file and folder sharing on Ubuntu Linux.

This is not the easiest way but it is the more comprehensive and less problematic solution.

After your fresh install of Ubuntu you need to install system-config-samba

```
sudo apt-get install system-config-samba
```

you can alternatively use synaptic or add\remove but you must chose specifically "system-config-samba" and if you use synaptic or add\remove you will see many other titles showing "samba" which may confuse the issue as we need specifically "system-config-samba"

now it is installed we need to launch the GUI

```
sudo system-config-samba
```

or go to "system\administration\samba

in the GUI;

click add folder, chose your folder,(ie.\home\public), - make it writeable and visible and under "access" make it accessible to all users to let other network computers access this new share folder.

under "preferences\security" change auth mode to "share"

then change the guest account to your ubuntu user name and you are done.

Don't need to logout or reboot.

I use this configuration to share files between linux - windows 7 - vista - xp - OSX

see attached photos for a more clear understanding. Where you see my user name, "drock", please substitute your own.

Not: This may not be the most secure method but it will get you running folder and file sharing straight away. For tighter security you can add password protection or a firewall but I recommend you only do that after you have gotten file sharing working with the above method. Once it works and you have tested it you can start increasing security incrementally so that if you lose the share you can simply go back one step and adjust as necessary. 

IMPORTANT:
If you have an open wifi connection any folders you share can be seen by anyone who drives by so be sure you only share folders like "Public" and don't put anything in there you don't have backed up somewhere else. 

I hope that helps

Powel

---

### Post by gordintoronto on 2009-10-31
Excellent, thanks!

---

