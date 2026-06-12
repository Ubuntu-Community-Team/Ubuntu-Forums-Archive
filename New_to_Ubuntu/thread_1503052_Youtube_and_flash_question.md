---
title: "Youtube and flash question"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-06-06
Anyone know why when using youtube, you cant select further into the track to skip ahead or go back in a video?  This was working fine in 9.10 but now isn't doing so hot in 10.04....

---

### Post by beew on 2010-06-06
Which browser do you use? I have the same problem with Opera but with Firefox it seems ok.

---

### Post by baddnady23 on 2010-06-06
Firefox.  I also have the 64 bit installation.

---

### Post by gandaran on 2010-06-06
> **baddnady23 said:**
> Firefox.  I also have the 64 bit installation.
and 64-bits adobe flash or the 32-bits flash from repos?

---

### Post by fooman on 2010-06-06
works ok here.  using 10.04, 64bit with the 64bit flash plugin.

---

### Post by baddnady23 on 2010-06-06
I thought 64 bit... but how do I tell?

---

### Post by sandyd on 2010-06-06
> **baddnady23 said:**
> I thought 64 bit... but how do I tell?
if your asking how to tell, its 32-bit.

To get 64-bit, see my signature (adobe flash tool) and download the appropriate version for your computer

---

### Post by gandaran on 2010-06-06
> **baddnady23 said:**
> I thought 64 bit... but how do I tell?
did you downloaded from adobe.com and manually installed it, or did you install it from the ubuntu repos, if you used the repos then surely you have 32-bits flash.

---

### Post by baddnady23 on 2010-06-06
> **gandaran said:**
> did you downloaded from adobe.com and manually installed it, or did you install it from the ubuntu repos, if you used the repos then surely you have 32-bits flash.

repos... I used carlee's fix and now some videos allow for me to skip ahead while others don't... I'll have to try the manual adobe install I guess.

---

### Post by formaldehyde_spoon on 2010-06-06
Fine for me.

---

### Post by tom.swartz07 on 2010-06-06
Theres a script that I pulled together from various places that will allow you to do a minimum interaction install of x64 flash.

[http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer)

Just download it and run it from the command line.

Save it to your /home folder as whatever you want, then run 
```
sudo ./FILENAME
```
from the terminal.

:D

---

