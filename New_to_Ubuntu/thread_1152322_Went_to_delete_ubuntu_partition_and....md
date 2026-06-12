---
title: "Went to delete ubuntu partition and..."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by The FrenchToast on 2009-05-07
Hey guys.  I Installed Ubuntu to my dell a few weeks ago and have been using it some.  I had it partitioned and dual booting with vista at startup. 

Well today i decided to just stick with vista, so i used Gparted to delete the Ubuntu partition.  I also deleted a very small partition that i assumed was part of Ubuntu or something

Now my computer won't boot into anything.  I think what i deleted was the GRUB (or whatever it's called)

the dell loadup screen comes up when i press the power button, immedietly followed by "GRUB loading...error 22"

If it helps, i still have the windows vista CD, although I'm pretty sure my current vista partition is still there and quite intact and i would rather just keep it as is.  

I think i just deleted an essential booter/loader of the OS.

Any help would be phenomonal

ps-i'm not too computer saavy, so if it gets too complicated

---

### Post by Didius Falco on 2009-05-07
Here is a simple tutorial on how to restore your MBR:

[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

Regards,

Didius

---

### Post by jacksinn on 2009-05-07
You'll want to use your Vista disk to recreate the MBR. Boot from the disk at startup and choose the recovery console. There should be steps you walk through to fix problems.

If you decide to try Ubuntu again, I suggest using the WUBI installer instead of creating partitions. This allows you to install Ubuntu via Windows, and if you for some reason don't like it, you can uninstall it just like any other program via the Add/Remove programs in the Control Panel.

---

### Post by The FrenchToast on 2009-05-07
> **Didius Falco said:**
> Here is a simple tutorial on how to restore your MBR:

[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

Regards,

Didius

worked like a dream! thanks

---

### Post by Didius Falco on 2009-05-07
Glad to help. Sorry Ubuntu wasn't for you at this time - maybe down the track, you'll get the urge to try it out again. :wink:

If you would, please mark this thread as solved - details on how in my sig.

Regards,

Didius

---

