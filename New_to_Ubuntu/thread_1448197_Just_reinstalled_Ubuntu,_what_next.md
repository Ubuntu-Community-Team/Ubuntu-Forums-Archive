---
title: "Just reinstalled Ubuntu, what next?"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by chiaboy on 2010-04-06
I had a big problem that I couldn't solve so just reinstalled a fresh copy on top of everything. So I'm back at square one.

What do I do first?

I've got a few articles that have some downloads, installs, upgrades, the one problem is the terminal command line is working weird (i.e. not working as it should). Sometimes I get the error message that I'm not running as root and the most recent error message reads:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


are there some basic stuff I should do first thing to make sure Ubuntu works as expected/well?

---

### Post by Elfy on 2010-04-06
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Generally this occurs when you have synaptic/add-remove/software centre/cli apt-get or aptitude running and try to start another one at the same time.

---

### Post by Jguy on 2010-04-06
Indeed, similar to some windows Installer processes, you cannot install/uninstall 2 programs at once.

Typically, after a clean install, I'll run updates for everything, and then install my basic programs, such as Banshee, Thunderbird, Filezilla, themes, etc. Install and update my video drivers through Restricted drivers and then restart the machine. Then that's it. :)

---

### Post by dearingj on 2010-04-06
> **forestpiskie said:**
> Generally this occurs when you have synaptic/add-remove/software centre/cli apt-get or aptitude running and try to start another one at the same time.

I've seen that happen when those programs aren't open, probably as a result of one of them accidentally not removing the lock.

@chiaboy: If you are **absolutely certain** that there are no software installers or updaters running, and keep in mind that Ubuntu may install software updates in the background depending on your settings, then you can manually remove the lock by using the following terminal command:
> sudo rm /var/lib/dpkg/lock

---

### Post by chiaboy on 2010-04-06
hmm...now I seem to get the original one (i.e it says I'm not root)

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

