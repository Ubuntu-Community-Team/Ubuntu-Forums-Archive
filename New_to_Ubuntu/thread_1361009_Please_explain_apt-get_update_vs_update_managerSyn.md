---
title: "Please explain: apt-get update vs update manager/Synaptic"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-12-21
Hi. I'm confused why when I run sudo apt-get update the update manager and synaptic both see upgradeable packages, but when I do sudo apt-get upgrade it says the packages are held back.

I got tired of update manager popping up every day for the last couple of weeks telling me that there were packages that I could upgrade (the kernel and some other stuff), that apt-get upgrade refused to install.  So today I just upgraded all that using synaptic (I know I could've just turned off update manager but I don't see the point).

I thought it was a dependency issue, but synaptic won't install packages that have missing dependencies will it?

The update included kernel 2.6.31-16-generic, but I don't remember what the rest of the update was.

Ubuntu 9.10

---

### Post by bodhi.zazen on 2009-12-21
See man apt-get, specifically the difference  between update, upgrade, and dist-upgrade :

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

> 
**update** update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the **location**(s) specified in */etc/apt/sources.list*. For example, when using a Debian archive, this command retrieves and scans the *Packages.gz* files, so that information about new and updated packages is available. An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress meter will be incorrect as the size of the package files cannot be known in advance. 


**upgrade** upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in */etc/apt/sources.list*. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be performed first so that **apt-get** knows that new versions of packages are available. 


**dist-upgrade** dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; **apt-get** has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The */etc/apt/sources.list* file contains a list of locations from which to retrieve desired package files. See also ***[apt_preferences]("http://linux.die.net/man/5/apt_preferences")**(5)* for a mechanism for overriding the general settings for individual packages.

---

### Post by blur xc on 2009-12-21
If you really want to get confused- see "man aptitude" and check out "aptitude safe-upgrade".  I'm still confused on what to use.  It seems the more I read on it, aptitude is better than apt-get?  

The multitude of ways to accomplish the same task in Linux is a bit overwhelming...

BM

---

### Post by Crunchy the Headcrab on 2009-12-21
> **bodhi.zazen said:**
> See man apt-get, specifically the difference  between update, upgrade, and dist-upgrade :

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

Oh, I read that before but I didn't really understand it.  If I'm understanding this correctly the reason why upgrade wouldn't install the new kernel was because the kernel was dependent on packages that were available, but not on my system (ie new packages)?

So running synaptic upgrade is more like doing a dist-upgrade?

Oh and thank you both for responding.

---

### Post by bodhi.zazen on 2009-12-21
> **Crunchy the Headcrab said:**
> So running synaptic upgrade is more like doing a dist-upgrade?

In a nutshell, yes.

Synaptic, apt-get, aptitude, these are all front ends for apt. So if you want to learn the gory details, you will need to start reading man pages.

---

### Post by slakkie on 2009-12-21
Try using aptitude (aptitude -s safe-upgrade). apt-get will not upgrade packages if they need to install new packages, aptitude does. If packages are held back that means that dependencies cannot be fulfilled and that the package will not be installed because of that. That is where synaptic comes in, it deals with these kind of issues so you don't have too.


You could force these upgrades, by running apt-get dist-upgrade or aptitude full-upgrade.

If you want to know the specifics, please have a look here: [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

