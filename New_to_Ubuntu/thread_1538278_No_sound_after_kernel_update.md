---
title: "No sound after kernel update?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by cjv8888 on 2010-07-24
After initial install of Lucid on my laptop CQ42-136TU, there was no sound.
Then I followed the steps here:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
to upgrade alsa and sound came.
After that, I did the initial update of the system which included a kernel update to 2.6.32.23 and the sound was lost again.(Alsa driver reverted back to 1-0-21)
I had to re-do the steps above which took a good while to do.  Now sound is perfect including speakers and headphones etc.
Now update manager is showing another kernel update to 2.6.32.24,
should I decline this kernel update?
Will I lose the sound again? and should I lock the kernel version for ever?

Thanks for any advice.

---

### Post by lidex on 2010-07-24
You don't **have to** update your kernel unless you have issues with the current one, at least in the short term. If you use the upgrade script here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
and don't delete anything, after a kernel upgrade all you have to do is:
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk). 

---

### Post by cjv8888 on 2010-07-25
> **lidex said:**
> You don't **have to** update your kernel unless you have issues with the current one, at least in the short term. If you use the upgrade script here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
and don't delete anything, after a kernel upgrade all you have to do is:

Thanks, I think I will just skip all the kernel updates for a while. Or will it hurt to lock version in the synaptic so the update manager will not keep on reminding?

---

