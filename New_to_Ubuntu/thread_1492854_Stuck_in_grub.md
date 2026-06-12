---
title: "Stuck in grub"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by redjess on 2010-05-25
Help please.

The last thing I did with my ubuntu (karmic koala) was install the updates and add a skype package.

Now my computer won't start ubuntu and is coming up with a lot of writing but the last bit of which says this...

"Since the script you are attempting to invoke has been converted to an Upstart job, you may use start(8) utility, eg. start S49console-setup start: Unkown job S49console-setup
* Speech-dispatcher configured for user sessions
* Starting the Winbind daemon winbind [OK]
*Starting common Unix Printing System: cupsd [OK]
*PulseAudio configured per user sessions
*Enabling additional executable binary formats binfmt-support [OK]
*Checking battery state... [OK]"

I am a bit of a beginner at this and I have no idea what any of this means. My pc is run off the mains so why would it check the battery state when there isn't one?!

Please help me!!

Jess

---

### Post by philinux on 2010-05-25
These messages come after grub. If the grub menu does not display hit the shift key after POST to get to it. Choose recovery mode then at the menu Resume normal boot.

---

