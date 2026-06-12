---
title: "Numerous KDE Updates?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2011-04-27
I was chatting on IRC today, and suddenly the update manager asked me to do a partial upgrade. I know that can cause trouble, so I denied it and looked to see what needed updating. There are 71 packages, most of them KDE. I don't even use KDE, except for maybe a few packages. Is one of them causing me to update kdebase-runtime, KDE 4 System settings, and libkdecore5 packages? I do not have a KDE repository in my software sources.

How can I keep Ubuntu from asking me to do a partial upgrade?
Should I permanently deny these KDE packages from being updated? How?
Will updating these packages cause harm to my computer?

Note: I accidentally did a partial upgrade a few months back but reversed most of the side effects. I'm hoping a full upgrade to natty will completely cure my system.

---

### Post by rosencrantz on 2011-04-27
I suppose they ship KDE 4.6 with Natty and rolled out the upgrade for Maverick now. I didn't see the upgrade, but I installed 4.6 from backports immediately after it came out.
Even if you just have a few KDE packages, chances are high that the dependencies include a large part of the KDE desktop.
I don't think there'd be a lot of harm in upgrading the KDE components if your KDE applications are part of the standard distribution and not 3rd party. If you want to block packages from upgrading, you can do that with
[FONT="Courier New"]sudo aptitude hold <packagename>[/FONT]
If you plan on upgrading to Natty soon anyway, the problem should go away, yes, but new partial upgrades like bugfix releases will happen from time to time.

---

### Post by EnigmaticCoder on 2011-04-27
Thank you. I'm going to wait for the release of natty. You've answered my question, but I'm going to wait until I upgrade to mark this thread as solved.

---

### Post by Paqman on 2011-04-27
> **EnigmaticCoder said:**
> 
How can I keep Ubuntu from asking me to do a partial upgrade?


Generally it's caused by the repos being a little out of sync. You did the right thing by declining the update. The problem usually sorts itself out if you wait a day and try again.

> 
Should I permanently deny these KDE packages from being updated?


No. If you have even one KDE app on your machine, you're likely to have a lot of KDE libs installed. That's just the way it is. Update them just like any other package.

This is the reason why some people don't like mixing apps from different DEs, but it's not exactly a big problem.

If you don't think you have any KDE apps that are depending on all this stuff, try running:

```
sudo apt-get autoremove
```

That will uninstall any packages on your system that aren't actually required by anything.

> 
Will updating these packages cause harm to my computer?

Nope.

---

### Post by EnigmaticCoder on 2011-04-27
Thank you for adding more clarity to the situation. Good to know that I can usually wait a day or so for the problem to sort itself out.

EDIT: Solved after upgrading to Natty.

---

