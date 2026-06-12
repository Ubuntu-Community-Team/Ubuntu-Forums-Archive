---
title: "Ubuntu Live usb boot restart problem"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Zombito13 on 2011-03-03
I'm not sure if this should be posted here, but I have an issue where when I restart the computer after using a live usb of Ubuntu 10.10 then windows will not start up until I restart it a second time.  On the second restart I have the option to restart normally or diagnose and repair.

Does not seem to have any permanent damage just doing boot normal but just wondered if anyone else ran into this problem before?

If there is another thread that solved this problem could somebody direct me?  I looked but did not see any.

---

### Post by Terry of Astoria on 2011-03-03
Try this:
After using Windows be sure to shut down cleanly before starting the Ubuntu boot; also at the end of your Live CD session, shut down instead of restarting. A lot of my machines have a problem with restarting similar to yours. A cold boot will be a clean one, I think. I doubt if Ubuntu actually touches your hard drive. I think Windows tries to restart, perhaps trying to recover from hibernation or sleep, fails due to the absence of hibernatory or sleepatory data or fails for whatever reason, and that's why upon the second restart, it prompts you with the menu for Normal Boot, Repair, etc.

---

### Post by Zombito13 on 2011-03-03
Thanks for the advice I will try tomorrow when I use same computer.  If it makes it any different I am using live usb not cd and it has persistent memory.  Doubt that makes a difference though from your advice.

---

### Post by Terry of Astoria on 2011-03-03
Perhaps removing the USB key entirely after halting might be recommended. (I don't know what your procedure was . .) Anyway good luck!

---

### Post by Zombito13 on 2011-03-04
Shutting down the computer and starting it back up did work.  My process before was just simple restart and leaving the usb in, and taking the usb out after restarted.  Both ways same results.  Cold boot worked, thanks for the help

---

