---
title: "Firefox not working after crash"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by hmo on 2009-06-28
Hi, I have ubuntu jaunty in my laptop sony vaio. Last day I was downloading something then the firefox hangs and stop working. I even restart the machine and every time I get the same error:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process or restart your system."

---

### Post by neogarv on 2009-06-28
Try going to the Processes tab in System Monitor (System > Administration > System Monitor) and look for Firefox. If there is an entry, press "End Process". Tell us the result of that.

---

### Post by lovinglinux on 2009-06-28
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

> **lovinglinux said:**
> 

**[size="5"][color=#CC0000]Troubleshooting[/color][/size]**

Several Firefox problems are related to corrupted profiles and can be easily fixed by restoring a profile backup (see Backup section), by deleting the corrupted profile or deleting specific files inside the profile. Usually, there is no need to re-install Firefox.

I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so deleting this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla.

You might need to kill Firefox before deleting the profile, as explained in the previous post.

---

### Post by sanderj on 2009-06-28
If restarting Ubuntu and killing the running Firefox process does not work, you can create a new profile using "firefox -profilemanager"

---

### Post by lovinglinux on 2009-06-28
> **sanderj said:**
> If restarting Ubuntu and killing running the Firefox process does not work, you can create a new profile using "firefox -profilemanager"

That work too.

or

```

firefox -P
```

---

### Post by mccartyj on 2011-11-09
firefox -P worked great for me in 11.10...

---

### Post by lovinglinux on 2011-11-09
This is a very old thread. Closing it.

---

