---
title: "[SOLVED] Howto install belkin F5D8053 without ndiswrapper"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2008-05-03
I have done the steps in the thread [http://ubuntuforums.org/showthread.php?t=766850](http://ubuntuforums.org/showthread.php?t=766850)
but my wireless antenna was still using the ndiswrapper.
So, I removed the windows driver and uninstalled the ndiswrapper in hopes it would now use the rt2870 driver..but no luck.
What steps am I missing to get it to use the linux drivers? (I don't want to use the ndiswrapper ..I suspect it's causing the frequent freezing)
Apologies for posting here, but forums won't allow me to post in absolute beginners section, I get an error.

---

### Post by Paris Heng on 2008-05-04
> **Jackie999 said:**
> I have done the steps in the thread [http://ubuntuforums.org/showthread.php?t=766850](http://ubuntuforums.org/showthread.php?t=766850)
but my wireless antenna was still using the ndiswrapper.
So, I removed the windows driver and uninstalled the ndiswrapper in hopes it would now use the rt2870 driver..but no luck.
What steps am I missing to get it to use the linux drivers? (I don't want to use the ndiswrapper ..I suspect it's causing the frequent freezing)
Apologies for posting here, but forums won't allow me to post in absolute beginners section, I get an error.

Just zd1211 in the Kernel. Overwrite it with zd1211rw firmware.

---

### Post by Jackie999 on 2008-05-04
While I thank you for your response..I'm afraid it's WAY over my head :)
I have the ralink native driver *I think* ..I'm hoping it's just a matter of getting linux to link it with the -

Bus 001 Device 002:  ID 050d:815c Belkin Components

---

### Post by altonbr on 2008-11-08
There is still no way to install this natively in 8.04 Hardy or 8.10 Intrepid as I am experiencing.

---

### Post by Jackie999 on 2008-11-12
Follow this thread for how to:

[http://ubuntuforums.org/showthread.php?t=919044&page=3](http://ubuntuforums.org/showthread.php?t=919044&page=3)

---

