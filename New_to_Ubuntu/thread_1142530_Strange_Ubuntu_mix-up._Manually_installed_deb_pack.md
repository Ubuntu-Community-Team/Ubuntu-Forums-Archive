---
title: "Strange Ubuntu mix-up. Manually installed deb package, replaced by other software"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by billgoldberg on 2009-04-29
after update.

The strangest thing just happened on Ubuntu 9.04.

I just installed the .deb package of HomeBank, the software needed to perform internet banking from the ING bank.

Everything worked ok (after some simlinks).

All of the sudden update manager pops up and tells me it has found updates for HomeBank.

I apply *(my spider sense should have gone off at that point, but it didn't)*.

Now when I try to launch homebank (through a custom made launcher in the menu) it says "file not found" (or something like that).

I browse to /opt where the folder was, but /opt is gone.

I "alt+f2" homebank and some personal accounting programs pops up.

What has just happened?

---

### Post by Tibuda on 2009-04-29
Looks to me that when you have updated it, it installed [this HomeBank]("http://homebank.free.fr/") over it.

---

### Post by billgoldberg on 2009-04-29
> **danielrmt said:**
> Looks to me that when you have updated it, it installed [this HomeBank]("http://homebank.free.fr/") over it.

Yes that what got installed.

--

Seems like a pretty serious screw up of the Update Manager.

Not only did it suggested updates for an application I don't have installed and installed the application.

But it also deleted the original program, located in /opt.

The /opt folder got created by the homebank.deb I installed and is no longer there after the update.

---

### Post by kpkeerthi on 2009-04-29
Sorry to hear that. But when apt* upgrades it actually performs a remove and install. The file locations of installed packages are stored in the local package repository and therefore apt was able to do a clean sweep of all the files when it upgraded. And since, unfortunately, the package names matched you lost the supposedly different homebank.

---

### Post by billgoldberg on 2009-04-29
> **kpkeerthi said:**
> Sorry to hear that. But when apt* upgrades it actually performs a remove and install. The file locations of installed packages are stored in the local package repository and therefore apt was able to do a clean sweep of all the files when it upgraded. And since, unfortunately, the package names matched you lost the supposedly different homebank.

I guessed that was what happened.

Off to launchpad.

---

### Post by markbuntu on 2009-04-29
You can lock a package in synaptic so it will never be updated. You should do that after you install the deb you had again.

---

