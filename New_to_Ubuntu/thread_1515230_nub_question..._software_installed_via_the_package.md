---
title: "nub question... software installed via the package manager, does it get updated?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by cragthehack on 2010-06-22
Like Netbeans 6.8 which is the version available now in the package manager.

6.9 is out. Does the package manager get the upgrade for distribution?

-Thanks...

PS. VERY new to linux. Still use me mac though :)

---

### Post by amauk on 2010-06-22
Probably not
(unless there's a compelling reason for an update, Ie. it's a security update)

There are two types of Linux distros
Fixed release distros
and Rolling release distros

Fixed release distros will freeze the packages in their software repositories, and maintain the same versions throughout the versions life-cycle.
This is desirable, as it ensures that at no point during the life of a release will a piece of software "break" due to an update.
(at least, that's the theory)

There are, of course, exceptions to this freezing process; but any updates that do get pushed through tend to be limited to bug-fixes and security updates only (rather than introducing new features)

Ubuntu is a fixed release distribution
(albeit with a short release cycle)

Rolling releases are the opposite
There is no (or very little) freezing of the software repositories
When a new version of AppX is available, it'll update on your system

Examples of rolling release distros include
Debian Testing / Unstable
Arch Linux

---

### Post by Paqman on 2010-06-22
Yes/no/maybe.

As mentioned above, if it's an important security update it *will* be pushed out to you. You also might get a new version of you enable the Backports repo (go to System > Admin > Software sources) Backports is there precisely to solve the problem of the standard repos getting stale, so it's particularly useful if you're running an older release (eg: Hardy)

The other option is to see if the devs have a PPA. A Personal Package Archive is like a mini repo that you can subscribe to. Many developers use them to push the latest version of their apps out to users.

---

