---
title: "How to undo software updates"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by eeprom on 2011-04-07
Hello,
I just allowed the software manager to install all the updates and my entire system is misbehaving.  First my wireless stopped working.  Then I notice when I try to shut down, the system begins to shut down and then stops on a screen I've never seen before.  There is a notice in the screen stating my username and the type of computer this is.  And in the lower right corner I have the option to Shut Down or Restart.  Neither of these do anything.  So I have to shut down by holding the power button down for a while.  When I restart, I don't get the normal start up / login screen.  I just go straight to my desktop.

Can someone tell me what happened and how to reverse it?  Does Ubuntu have a system restore?

thanks,
EE

---

### Post by Mark Phelps on 2011-04-07
Sorry, there is no equivalent to System Restore built into Ubuntu.

You could try rolling back individual updates, but that is really major, and risky, work.

The only safe way to do this is to reinstall.

---

### Post by rosencrantz on 2011-04-07
You can at least try some analysis. Check /var/log/dpkg.log
(e.g. type [FONT="Courier New"]cat /var/log/dpkg.log | egrep 'install |upgrade '[/FONT] on the command line)
You should get output like this:
2011-04-07 10:53:00 upgrade phonon 4:4.7.0really4.4.4-0ubuntu1~maverick1~ppa1 4:4.7.0really4.5.0-0ubuntu3~maverick1~ppa1
which translates to:
date time operation package version/repository-old version/repository-new
If you can track down your problematic upgrades to a specific repository, you could try disabling it and do 
[FONT="Courier New"]sudo apt-get update
sudo apt-get dist-upgrade[/FONT]
I'm not quite sure whether dist-upgrade can actually revert. 
You might have to use pinning. [http://ubuntuforums.org/showthread.php?t=432636](http://ubuntuforums.org/showthread.php?t=432636)
Look out for dependency issues, but if you are considering a reinstall anyway, it can't hurt to play around a bit. If you don't have a separate /home partition, back up your home directory before doing major system changes.
If you are unsure what to do, attach /var/log/dpkg.log and /etc/apt/sources.list to your next post.

---

