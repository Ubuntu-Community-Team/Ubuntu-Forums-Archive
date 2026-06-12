---
title: "Keeping ClamAV up to date?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-07-11
I use ClamAv. It was installed through Synaptic. I went to do freshclam today and learned that I had an out of date clam. Reading here

Upgrade Instructions
[http://wiki.clamav.net/bin/view/Main/UpgradeInstructions](http://wiki.clamav.net/bin/view/Main/UpgradeInstructions)

here

Ubuntu
The Ubuntu packages are maintained by Ubuntu MOTU Developers. ClamAV has been officially included in the Ubuntu distribution since the first Ubuntu release. Run apt-cache search clamav to find the name of the packages available for installation.

There are two classes of clamav packages available for Ubuntu users:

The released set (release, *-updates, and *-security) are patched for security updates. Following extensive testing of clamav and the packages that use it in the backports repository, they may be updated to a newer version. These are official Ubuntu packages and supported by community developers.

The Ubuntu backports repository will contain the newest clamav version that has been at least lightly tested to work with that version. These packages can be installed by enabling the backports repository in your system. These are official Ubuntu packages and supported by community developers.

and here

Production quality releases
Latest stable release: xxxxxxx
[http://www.clamav.net/download/sources](http://www.clamav.net/download/sources)

I got LOST. The more I read, the less I understood. I tried to use Synpatic to uninstall and re-install Clam. I did the "Update" first, twice and got nowhere. Once Clam was re-installed it still said I had an "out of date" package. By the way: it's 95.2 instead of 95.1, so not a huge difference.

What am I doing wrong? How do I update or remove & upgrade to the 95.2 version?

Is this supposed to happen this way? I guess I'm asking what's the easiest way to resolve this?

Thanks, community.

---

### Post by 73ckn797 on 2009-07-11
I have had the same issue and if I was using the 32 bit 9.04 I would use Avast which updates itself with no problem. They do not have a 64 bit version. Not that I need anti virus but I would like to have it on if I suspected the need for it and know that it would be up to date.

---

### Post by mike2357 on 2009-07-11
If you are running freshclam, then your virus signature files are up to date.  It's only the anti-virus programs that aren't the latest version.  Although I can't guarantee it, I doubt it will be a problem.  Ubuntu will eventually upgrade the clamav programs, but it may not be until the next version comes out this October.

In the past I downloaded the latest version from clamav's web site, re-compiled their programs in /usr/local, and then set Unbuntu's startup scripts to point to the the version I downloaded and compiled.  It's a multi-step procedure, and I haven't done it for awhile.  Now, I'm OK with just running freshclam to update virus signature files and waiting until Ubuntu upgrades to the latest software version.

---

### Post by Najand on 2009-07-11
As "mike2357" said, while you are running freshclam, then your virus signature files are up to date. So there are usually nothing to worry about. However if you want to use the newer version you should install it from source, or make the package yourself.
Check the link below:
[http://wiki.clamav.net/bin/view/Main/UpgradeInstructions](http://wiki.clamav.net/bin/view/Main/UpgradeInstructions)

---

### Post by Mark_in_Hollywood on 2009-07-12
Thanks, Najand & Mike, that's what I needed to know.

---

