---
title: "Systemsettings will not run in KDE4/Jaunty"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by jfkuhn on 2009-06-15
I am having a problem with system settings.  It will crash giving an error similar to this thread:

[http://ubuntuforums.org/showthread.php?t=767493&highlight=systemsettings](http://ubuntuforums.org/showthread.php?t=767493&highlight=systemsettings)

the message is "caused the signal 11 (SIG SEG V) and it will not generate any debugging code.

However, it DOES run if I use 'kdesudo dbus-launch systemsettings'.  But this only lets me change the system settings for root, not for the user.  I have tried to purge it as in the thread above and re-install it but it still won't go.  Otherwise the system is very stable.  I am running compiz and nvidia on Kubuntu Jaunty, but I tried this without compiz and it still crashes (anyway, I can run it as is with kdesudo).  It seems to be related to permissions.

KDE4 in general just seems to have a real hard time allowing anything to run as root, it is very disappointing since this was so well implemented in 3.5.

Any ideas?

---

### Post by jfkuhn on 2009-06-16
OK, I finally got it figured out.  I found the bug thread which for some reason eluded me before in all the many pages I read on this subject, which can be found here:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/366542](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/366542)

the culprit was /home/.kde/share/apps/systemsettings/systemsettingsui.rc

Once this file was deleted, system settings ran normally.  I should also note that I did a fresh install when I upgraded to Jaunty, but I only formatted my root partition, and a lot of old settings were saved in my /home partition.  This turned out to be useful for recovering my old program preferences after the upgrade, but problematic in those cases where an old config conflicts with the way things are done in 4.2.  Maybe the best advice is to delete those prefs except for the programs (such as Kate and firefox) which you know will work.

---

