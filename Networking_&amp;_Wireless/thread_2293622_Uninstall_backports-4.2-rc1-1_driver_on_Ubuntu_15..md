---
title: "Uninstall backports-4.2-rc1-1 driver on Ubuntu 15.04"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by srikesh2 on 2015-09-06
Hello all,

I have a no-name (make & model unknown) bluetooth dongle that I was hoping to set-up with my otherwise normally working desktop (Ubuntu 15.04).  I searched online and found a solution that had worked for someone else ([http://ubuntuforums.org/showthread.php?t=2251009](http://ubuntuforums.org/showthread.php?t=2251009)).  The solution was to install the latest backports driver......so I downloaded backports-4.2-rc1-1 from the link ([http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)) and proceeded to follow the instructions in the link.  After rebooting, my wireless device is no longer recognized by Ubuntu.  How can I reverse (uninstall the just installed driver package) the installation?  The documentation site for the backports doesn't seem to have uninstall instructions and I did not find a readme file in the folder with any such instructions. I'm hoping that uninstalling the backports driver and rebooting will return my desktop to its prior state.  Please help!.

Srikesh

---

### Post by jeremy31 on 2015-09-06
You need to get into the directory with the backports source code ```
cd backports-4.2-rc1-1
``` and ```
sudo make uninstall
``` and reboot

Post ```
lsusb
``` and we will see if bluetooth can be fixed

---

### Post by srikesh2 on 2015-09-06
Thanks, jeremy31.  That did the trick.  My wireless device is working now.  Everything else seems to be like it was before.

Regarding the blue tooth dongle, I would love to get assistance from you or others in the community to get it to work.  My guess is that I will have to start a new thread.  Is 'Networking & Wireless' the right section to seek assistance on troubleshooting hardware (blue tooth 4.0 dongle)?

---

### Post by jeremy31 on 2015-09-06
> **srikesh2 said:**
> Thanks, jeremy31.  That did the trick.  My wireless device is working now.  Everything else seems to be like it was before.

Regarding the blue tooth dongle, I would love to get assistance from you or others in the community to get it to work.  My guess is that I will have to start a new thread.  Is 'Networking & Wireless' the right section to seek assistance on troubleshooting hardware (blue tooth 4.0 dongle)?

It belongs in wireless and you could just edit the title and continue on this thread

---

