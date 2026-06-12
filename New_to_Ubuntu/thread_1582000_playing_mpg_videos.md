---
title: "playing mpg videos"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by mhammann57 on 2010-09-25
Hello,
 
What do I need to do so that I can play an .mpg video file?  I have Ubuntu 10.  It plays .avi videos but not the .mpg videos.
 
Thanks,
 
Mark
McKinney, TX

---

### Post by roccivic on 2010-09-25
Try opening a terminal and typing in:[PHP]sudo apt-get install ubuntu-restricted-extras[/PHP]

---

### Post by lyall on 2010-09-25
see the following link [https://help.ubuntu.com/community/RestrictedFormats/MP3]("https://help.ubuntu.com/community/RestrictedFormats/MP3")

hope this helps

good luck and have fun learning

---

### Post by mrhhug on 2010-09-25
```
sudo apt-get update
```

```
sudo apt-get install vlc vlc-plugin-esd
```

VLC is great for everything

---

### Post by mhammann57 on 2010-09-26
Thanks to all.  Went with restricted aps.  Everything works.  Question though.....what did I just install?  And, can it be reinstalled or uninstalled if I have problems in the future?

Thanks again.  Gettin' to like this Ubuntu thing.  Billy Gates, you're in trouble!

Mark

---

### Post by Vaphell on 2010-09-26
restricted extras installs many patent/royalty encumbered codecs that can't be distributed by default on ubuntu disks without Canonical (company that manages ubuntu) paying significant amounts of cash. That's the price of having $0 operating system.

---

