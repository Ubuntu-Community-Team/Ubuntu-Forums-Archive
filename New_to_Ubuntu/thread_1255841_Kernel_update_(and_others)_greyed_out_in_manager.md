---
title: "Kernel update (and others) greyed out in manager"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by landman 1560 on 2009-09-01
I have been looking at a kernel update for over a month that is greyed out.  I'm currently on 2.6.28-13.  I've attached a screenshot of the manager.

I tried removing some of the repos that aren't necessary and that didn't open it up.  I'm not real good with this part in Ubuntu yet.  I could really use some suggestions on this issue.

---

### Post by dearingj on 2009-09-01
Open up Synaptic Package Manager, find one of the packages that you can't upgrade, and attempt mark it for upgrade. Synaptic will tell you that it depends on some other package that can't be upgraded. Find that other package, attempt to mark it for upgrade, etc, etc, keep going until you get to a package that you can't upgrade because you have the latest version or until you get a different error message. Then post here which package or what the error message is.


Example: I'm facing a similar problem with openoffice.org (I'm alpha testing the next version of Ubuntu, so I expect my problem will be fixed quickly): I can't upgrade openoffice.org because it depends on openoffice.org-core. I can't upgrade openoffice.org-core because it depends on openoffice.org-common. I can't upgrade openoffice.org-common because there is no upgrade for that yet.

---

### Post by bumanie on 2009-09-01
In terminal > sudo apt-get update && sudo apt-get upgradeThen answer y and hit enter. Updates should download and update manager GUI should work again.

---

### Post by jatinps on 2009-10-05
i am on karmic beta (fresh install) and after few days of updates, I have 'ubuntu-desktop' grayed out in update manager. I checked in synaptic and almost everything is a dependency on ubuntu-desktop, so not really sure.

---

