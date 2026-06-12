---
title: "[SOLVED] After system update, Ethernet stopped working"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by flamingsole on 2008-02-12
Hello,

I'm running Gutsy Gibbon. Today, when I booted into my system there were some software updates. I believe they were related to the Linux core, but I can't remember the exact names of the packages. I'm sure there is a way to see this after an update has run, but I'm not sure what that is.

Anyway, upon installing the updates, I was asked to restart. I did so, and now my Ethernet connection is gone. The last time there was a similar update (maybe a week or two ago), this happened and I followed the steps detailed at [http://ubuntuforums.org/showthread.php?t=186430]("http://ubuntuforums.org/showthread.php?t=186430"):
> 
First, you need to add dmfe to /etc/modules. To do this you need to open up modules with gedit by typing the following code into a terminal.

Code:
```

sudo gedit /etc/modules

```
Then, you need to add "dmfe" to this, without the quotes. Make sure you save.

Finally, you need to blacklist the tulip driver so it wont run at startup. To do this you need to run the following in a terminal.

Code:
```

sudo gedit /etc/modprobe.d/blacklist

```
After this is opened, you need to add "blacklist tulip", without the quotations, somewhere in the file. Then save.

After both of these steps have been completed, restart your system, and voila, you now magically have a working ethernet adapter.


This worked perfectly, although I don't actually have a Davicom ethernet adapter (I have an Intel ethernet adapter). I tried reversing this today, and rebooting, but still have no connection. Any thoughts on this?

Thanks,
Jon

---

### Post by flamingsole on 2008-02-13
Interestingly, when I turned on my computer today, everything seemed to be working perfectly. Solved, I think.

---

