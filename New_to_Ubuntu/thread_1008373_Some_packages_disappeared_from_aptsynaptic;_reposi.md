---
title: "Some packages disappeared from apt/synaptic; repositories intact"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by IConrad01 on 2008-12-11
[COLOR="Red"]**|EDIT|**[/COLOR]
The Debian repository has changed; libboost1.36 is now kfreebsd architectured.  I'm pretty sure this would prevent it.
[COLOR="Red"]**|/EDIT|**[/COLOR]

Hello; and thank you to anyone and all who give this their attention.

I am using Ubuntu 8.10 on a Dell Inspiron 1720.

I recently did something I know is inadvisable, though it should not have had the effect it does; I added the Debian unstable repository to my sources.list file.  I did so while creating an Apt-pinning profile to prevent any "upgrades" from registering w/ I enable the unstable repository.  I was specifically after the libboost1.36 files, which are part of the Debian unstable repository but not part of the Ubuntu repository.

(Despite apt-pinning to lower the Debian repository to the lowest priority, I also leave it commented out at all times except for when I intentionally pull from it.)  I did ***not*** acquire the GPG key -- so I could ensure that no packages from Debian were installed accidentally.

With all of that background, here's my actual problem:

I was in the process of compiling [FreeOrion](http://www.freeorion.org/index.php/Compile); while compiling GG the boost libraries were found and complete. When I went on to compile the actual game, scons could not find the boost libraries.

Upon attempting to re-install the packages, I discovered that they were 'no longer available' in the repository no matter how often I re-enabled the Debian repository and re-loaded synaptic. The packages remained in synaptic until I keyed them for removal, and now they do not appear at all.

Other packages from Debian unstable appear; so far it seems **only** the boost 1.36 libraries have vanished.  I checked, and they remain part of the Debian unstable repository; so it has to be something I am doing.  I also tried removing the apt pinning profile, to no avail.

Is there someone out there who has encountered something similar before?  

Please advise; and again, thank you!

---

