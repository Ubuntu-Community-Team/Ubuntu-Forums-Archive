---
title: "Strange problem with desktop"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by spribo on 2009-10-31
I recently did a clean install of Ubuntu Karmic over Ubuntu Jaunty. Upon installing Jaunty, the whole desktop was moved slightly to the left, resulting to a thick black zone in the right. However, I installed Nvidia 185 and, after modifying the resolution, and rebooting, this problem didn't appear again. Until today, this time with Ubuntu Karmic. I installed again Nvidia 185 (the recommended), I changed the resolution, and suddenly Ubuntu interface was "turned into" an older version: everything looked like Ubuntu 5! After rebooting, interface became again normal, but the thick black zone was there! What can I do? Thank you very much for your help!

---

### Post by spribo on 2009-10-31
Please, I need help!

---

### Post by Oropher8598 on 2009-10-31
The off-center display with a black line around one or two sides means the nVidia driver has mis-detected your monitor's refresh rate. (I get that too.) Usually, in the Display Preferences app (*System -> Preferences -> Display*), one of the options in the 'Refresh Rate' dropdown will put everything in the right place.

When you launch Display Preferences, Ubuntu may suggest you'd like to use the nVidia settings app instead... but for something like this I usually find Display Prefences is easier ;)

---

