---
title: "Updating Gnome"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Shmook on 2009-03-20
Hey I noticed there's a new version of Gnome out (2.26) and also that my current version is 2.24.1, and also that when I ran the update manager updating gnome wasn't an option.

Is it just that it's not in the repositories yet? Or do I update in some other way?

---

### Post by taavikko on 2009-03-20
GNOME 2.26 is available only in future release of 9.04 Jaunty Jackalope.

It is not going to be available in Intrepid 8.10 release.

When the 9.04 is released, you have an option to upgrade to it, using update-manager.

---

### Post by Shmook on 2009-03-20
Okay thanks for the info--and just a quick follow-up about gnome and I guess desktop enviros in general:

why isn't this a simple update like basically everything else in ubuntu? Are there intense system alterations made by changing the version of gnome, or kde or xfce for that matter? 

For certain I'm new to Linux but it seems like if you can update the kernel so easily a desktop wouldn't be much more difficult.

---

### Post by taavikko on 2009-03-20
Desktops are so complex and huge entities that full upgrade is major change and affects almost everything.
It's hardly worth the hassle to try to update an older release (8.10)
than offering a new one that is built around it entirely.

Kernel upgrades after release are most of the time, minor tweaks and such.

Sorry if this sounds little confusing, haven't woke up yet :)

---

### Post by Shmook on 2009-03-20
That's okay, thanks a bunch, I didn't realize the desktop was so heavy...that sounds like a weird metaphor :-k

---

### Post by mcduck on 2009-03-20
> **Shmook said:**
> Okay thanks for the info--and just a quick follow-up about gnome and I guess desktop enviros in general:

why isn't this a simple update like basically everything else in ubuntu? Are there intense system alterations made by changing the version of gnome, or kde or xfce for that matter? 

For certain I'm new to Linux but it seems like if you can update the kernel so easily a desktop wouldn't be much more difficult.
Actually you don't get that much program updates in Ubuntu at all..

The main rule is that all program versions are locked at the end of Ubuntu release's development, and after that only updates are to fix serious bugs and to provide security fixes. Never to provide new features, they are added to next Ubuntu release.

The Backports repository helps a bit, as it includes some new packages from the development versions of Ubuntu, but only packages with few dependencies and little or no changes to the rest of the system are allowed in Backports so most of new programs are not backported. If you want to always have the latest program versions you should use some rolling-release distribution.

Updating the DE is neither a bux fix nor security update so it won't happen, not in Ubuntu.

---

