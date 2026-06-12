---
title: "help cant watch u tube vids.."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by deathseek on 2010-01-12
where can i download a flashs pluginns for ubuntu:popcorn:

---

### Post by bcn17 on 2010-01-12
go to medibuntu.org

Follow their directions for installing their repository. 

Then, type this:

>sudo aptitude install ubuntu-restricted-extras w64codecs

**If you have a 32-bit processor replace the 64 with 32.

---

### Post by fancypiper on 2010-01-12
You may have to do this as well.  I'm not sure you need it in 9.04, but I had to for 9.10

# As per [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
# Howto fix Flash on Ubuntu 9.10
If you are not able to click on flash (e.g. on Youtube), here is how to fix this known bug (works for both 32-bit and 64-bit):
1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1
3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

---

### Post by lawenlerk on 2010-01-12
What i did is go to Applications->Ubuntu software center and search for flash and install the "Adobe Flash plugin". 

Just to make sure, close firefox while its installing.

---

### Post by MelDJ on 2010-01-12
or get the deb from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by jmore9 on 2010-01-12
Go here and follow the the instructions provided :

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

