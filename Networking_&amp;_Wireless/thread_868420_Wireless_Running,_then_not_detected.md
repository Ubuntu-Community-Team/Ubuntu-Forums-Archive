---
title: "Wireless Running, then not detected"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Speur18 on 2008-07-23
I followed this guide here, to install my onboard broadcom Wifi on my Compaq F558us Notebook with 8.04 x32.  Just this past week, I turned on my laptop, and was shocked to see that my wireless card was not detected in lspci.  I uninstalled ndiswrapper, and all packages associated with it, reinstalled it, and was glad to see that it worked.  Turned it off, turned it back on, wireless still working.  The Next day, I turn on my laptop to see that lo and behold, no wifi once again.  Any idea as to what is happening?  I didn't do any severe kernel updates.

---

### Post by toylas on 2008-07-23
I have a similar problem (though not exactly the same) and I just posted it 5 minutes back in this thread

[http://ubuntuforums.org/showthread.php?t=868418](http://ubuntuforums.org/showthread.php?t=868418)

Keep an eye on it too cuz somebody might post something there.

---

### Post by Speur18 on 2008-07-23
Thanks. And will do!

---

### Post by toylas on 2008-07-23
Hey my problem was actually not a problem as I had anticipated. I was being stupid and was not specifying that the WEP key was hex. Anyways, by now you would have guessed that I'm not an expert but I guess some things I would look at are:

ifconfig and "lshw -C network"

See if it lists wireless in the capabilities. We could try to figure something out from there. Maybe some experienced people will tell us some more diagnostics.

Toylas

---

