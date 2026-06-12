---
title: "failed installation"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by acimna on 2009-07-26
Three attempts to install Ubuntu 9.04 from a CD supplied by Canonical failed at different install percentages (above 50%), each time due to a different file not being compatible.
It's a new 500GB, 4Ghz machine supplied with XP Pro and Office 2003 "demo software" which I wanted replaced with Ubuntu.
The result is ... well, no workable computer.
I'll try to install Suze later today from a loaned disk and give the Ubuntu disk to an ICT guy tomorrow for him to try installing it on another machine.  This way we check both machine and disk.
Any other advice I can try out in the meantime?
Also, Ubuntu icons and layout are too big and loud - cluttering up workspace.  It is not nearly as attractively petite (to me anyway) and practical as is Suze's appearance.  I hope the desired appearance can be achieved by a simple adjustment.

---

### Post by LookTJ on 2009-07-26
There has been reported bugs of Ubiquity(which is the installer gui for Ubuntu) failing at about 70%. I had experienced this same bug. 

The workaround according to some is installing using the alternate cd.

---

### Post by mikechant on 2009-07-27
> The workaround according to some is installing using the alternate cd.

Yes, I'd second that - the alternate CD got me through various install problems a few releases ago.

---

### Post by fbugnon on 2009-07-27
> **acimna said:**
> (...) give the Ubuntu disk to an ICT guy tomorrow for him to try installing it on another machine.  This way we check both machine and disk.
Any other advice I can try out in the meantime?
Also, Ubuntu icons and layout are too big and loud - cluttering up workspace.  It is not nearly as attractively petite (to me anyway) and practical as is Suze's appearance.  I hope the desired appearance can be achieved by a simple adjustment.

When booting from the Ubuntu-CD there is an option to check the disc, you can do this to make sure it's OK, although I never had a problem with the CD provided by Canonical.

The big icons and layout I think you can adjust in the Video Preferences (found in the menu Systems > Preferences > Screen/Video - sorry I'm not using English installation so I'm not sure about the correct terms).

---

### Post by ranch hand on 2009-07-29
When booted to your Live CD go to go to terminal (applications->accessories->terminal) and;
```

sudo apt-get install ubiquity

```
Try your install again.  It will probably work.

---

