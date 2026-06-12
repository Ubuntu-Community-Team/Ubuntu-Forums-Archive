---
title: "Splash with Terminal window gone"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by doninsa on 2010-05-16
Upgraded to grub2 version 1.98.16 and lost the neat splash that shows a small terminal window with commands scrolling.  Looked at the grub2 configuration files including 05_debian_themes but couldn't find it.  Remembered to run update-grub after all changes.  Still - no joy finding the old splash with the terminal window.  Using lucid lynx 10.4. TIA  Don

---

### Post by corncob on 2010-05-17
> **doninsa said:**
> Upgraded to grub2 version 1.98.16 and lost the neat splash that shows a small terminal window with commands scrolling.  Looked at the grub2 configuration files including 05_debian_themes but couldn't find it.  Remembered to run update-grub after all changes.  Still - no joy finding the old splash with the terminal window.  Using lucid lynx 10.4. TIA  Don

Just a thought:  Install StartUp-Manager
```
sudo apt-get install startupmanager
```
Then go to System > Administration and run it.  See if there's anything there that's helpful.

---

### Post by doninsa on 2010-05-17
> **corncob said:**
> Just a thought:  Install StartUp-Manager
```
sudo apt-get install startupmanager
```
Then go to System > Administration and run it.  See if there's anything there that's helpful.

I have Startup_manager installed and I also have the box checked for "show text during boot."  I think there's something in my grub2 configuration that fails right after I press enter to select an operating system. Thanks for taking the time to understand my question and coming back with a reply.  This is a tough one.  Regards - Don

---

