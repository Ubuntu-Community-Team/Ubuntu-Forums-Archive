---
title: "[SOLVED] clean up program needed"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by dog-soldier on 2008-12-18
im using ubuntu 8.04 and like the title says im in need of a program that cleans up anything that is left from a uninstall. i think i remember reading on a forum someplace about a program that does it but cant think where i read it at.

thanks in advance

---

### Post by kanikilu on 2008-12-18
Not sure if this is exactly what you are looking for, but see this article for general routine maintenance/cleaning tips:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by Paqman on 2008-12-18
Try gtkorphan, it'll find and remove any orphaned packages left over from uninstalls.

---

### Post by Therion on 2008-12-18
You're looking for **QuickStart** maybe?  You can get that here: 

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by donkyhotay on 2008-12-18
I use gtkorphan combined with 
```
sudo apt-get autoremove
```
and
```
sudo apt-get autoclean
```

---

### Post by OrangeCrate on 2008-12-18
In addition to what has already been said, this should help...

**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by thunk77 on 2008-12-18
Also, there is an application called FSlint (File System Lint) which MAY be what you are looking for. It is in the repositories.
BUT (and I cannot stress that enough) you should be very careful when using it as you could damage your system!!
If what you are looking for is a simple system cleanup, then the above posters informed you excellently and you should follow their instructions.

---

### Post by dog-soldier on 2008-12-18
thanks again everyone. the program i heard about was FSlint. i tried everything there and got almost everything out. the one thing thats a real pain is opera. it messed up on me yesterday and i was trying to get every bit of it out so i can reinstall it but no go so far. but ill keep trying .
opera is doing a little better but not 100%

---

