---
title: "Cleaning up packages  - conflicts?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by carbon512 on 2011-02-11
In trying to troubleshoot and fix an audio problem, I installed all  kinds of other packages that interfered with other things. I have mostly  removed them, and reverted to my 2.6.32-28-generic kernel.

I  know that the backport generic meta-package is supposed to manage updates, I am concerned that I have subverted it.

Question - I have still currently installed:
linux-backports-modules-alsa-lucid-generic, version 2.6.32.28.32
and
linux-backports-modules-alsa-2.6.32-27-generic
linux-backports-modules-alsa-2.6.32-28-generic

Should I remove the older linux-backports-modules-alsa-2.6.32-27-generic ?
Or does the new version supersede it?

Also,  I see that linux-backports-modules-headers-lucid-generic, version  2.6.32.28.32 is NOT installed... but there are several flavors of  linux-backports-modules-xxx-lucid-generic, version 2.6.32.28.32 that are  not installed. Maybe I don't need them.

My sound card basically  functions, just has a weird issue that needs addressing and I am trying  to figure out how to understand what I am getting when I follow the  steps at [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) . I did see that there is some discrepancy between driver version and  library version for my card. I am hoping that I can take care of this  easily through simple package updates and installs, so I can take a  break from clawing my way up the learning curve (which is fun but  exhausting.) 

thanks as always. Walking the fine line between figuring it all out my own and asking for help... HELP.

---

