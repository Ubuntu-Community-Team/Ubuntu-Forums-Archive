---
title: "Why is Power Management not setting?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by usererror on 2008-12-31
I have been dealing with a problem where I set up my monitor to go to "sleep" after xx minutes via ScreenSaver, then clicking Power Management.  But it never worked.  It just blacked the screen.

Then I found this post:

[http://ubuntuforums.org/showthread.php?t=394942](http://ubuntuforums.org/showthread.php?t=394942)

that states if you use the **xset** command you can set the time (in seconds) for suspend, sleep, off, and I did that and it works great!

But how come it doesn't do that via the GUI?

I did a Dist-Upgrade from 7.10 to 8.10.  Could it be from the upgrade?

Thanks in Advance!

---

### Post by mikewhatever on 2008-12-31
Did you say the screen blacked? What else did you expect?

---

### Post by usererror on 2009-01-23
> **mikewhatever said:**
> Did you say the screen blacked? What else did you expect?

I expected it to go into power save mode, like I wanted it to.  Not just put a black screen saver up basically.  

Now it works like it should my monitor LED indicates it's in sleep mode (goes amber) instead of staying blue, with the xset mentioned in the post above.

---

