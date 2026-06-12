---
title: "Pidgin stopped working after a load of updates."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-29
After a ton of updates Ubuntu 8.10 gave me (like 70), Pidgin got uninstalled. So I go to Add/Remove and try to install, and then I get this:

Cannot install 'pidgin'

This application conflicts with other installed software. To install 'pidgin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

So I go to Synaptic Package Manager to download Pidgin there and mark for complete installation. Then I get this:

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all repositories are added and enabled in preferences.

pidgin:
 Depends: libpurple0 but it is not going to be installed
 Depends: perlapi-5.8.8  but it is not installable

Then I went to try to install libpurple0. It won't work either. What do I do?! This is making me sooo mad.:(

Thanks for your help and time :D

---

### Post by gymophett on 2009-01-29
Solved!!

---

### Post by zabien1970 on 2009-01-29
Just curious, how did you solve this?

---

### Post by akwala on 2009-02-15
This is the second place I've seen someone report this problem with installing Pidgin in Intrepid, where the problem seems to have miraculously resolved itself.

I saw the same dependency complaints when I tried installing Pidgin via Synaptic, after a fresh 8.04->8.10 upgrade.

Here's what I did to fix it based on info I gathered from various sites/forums:

1. Uninstall the existing Pidgin version and all the software that it depends on -- in my case, pidgin-data was the only one.

2. Install libsilc-1.1-2 via Synaptic -- libpurple0 (see below) apparently depends on it.

3. Download the following 4 pkgs from [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) -- in my case, Pidgin 2.5.4, for Intrepid 64bits.
- pidgin
- pidgin-data
- libpurple0
- libpurple-bin

4. Install the above downloaded pkgs in the following order:
- pidgin-data
- libpurple0
- libpurple-bin
- pidgin

After doing the above, Pidgin seems to be running fine.

Something seems to be wrong with the dependencies of the same pkgs in the channel (Synaptic). Incidentally, Update Manager now shows libpurple0 and pidgin, but they're greyed out, and it says that my system is up to-date. Synaptic shows these 2 pkgs as *installed (upgradable)*, even though the version I installed is the same as that in the channel. I tried upgrading them, once again, via Synaptic, and saw the same complaint about the dependency on libper5.8 & perlapi-5.8.8.

---

