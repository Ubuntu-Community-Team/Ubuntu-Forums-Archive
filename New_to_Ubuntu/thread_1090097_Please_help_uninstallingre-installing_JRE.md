---
title: "Please help uninstalling/re-installing JRE"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by xXNI4NI on 2009-03-07
OK, so I am new to Ubuntu and slaved getting everything just right and am satisfied except w/ my java. I have read and re-read all over these forums and other forums and attempted to watch a video on youtube :( to no prevail now I am stuck w/ a "form" which I believe does not help at all. In firefox about : plugins the "java" i have right now is GCJ Web Browser Plugin (using IcedTea) 1.0, and it does not work. SO i tried to remove it in add/remove programs and get the message "
One or more applications depend on sun-java6-bin. To remove sun-java6-bin and the dependent applications, use the Synaptic package manager." so i headed to synaptic and there was nothing... really what i would like to do is get a fresh start, and re-install it. It seems though alot of How To's are out of date if ANYONE knows of one that would work for me i would appreciate it.
Ubuntu 8.04 x64

---

### Post by ivanvajar on 2009-03-07
You must be sure that you don't have two flash plugins installed in Mozilla. flash-plugin-nonfree is recomended by many users here. In several cases the conflict was solved by removing gnash and swfdec

---

### Post by ivanvajar on 2009-03-07
Be sure you have ubuntu-restricted-extras installed

---

### Post by ivanvajar on 2009-03-07
I just saw that you are running on x64. Make sure you install x64 plugins. Sorry.

---

### Post by xXNI4NI on 2009-03-09
thanks i have flash-nonfree its the java i would like, i did not know about the ubuntu-restricted-extras so i grabbed it from synaptic :) very nice never knew about it...i saw on ubuntu that it came w/ java sun-6 but under synaptic i didn't see it included, we'll see how it plays out but ill check it for updates and get back...

---

### Post by taurus on 2009-03-09
I don't believe java plugin for x86_64 is included in the repos.  You need to download and install it by hand from Sun's site.

---

### Post by xXNI4NI on 2009-03-09
OK so I installed the ubuntu-restricted-extras package via synaptic, did a complete removal of my gcj which did remove itself from about:plugins so now i need a plug in that will work. Sorry if this has been aked before but i cannot find the solution anywhere oh and btw i don't remember where i read i think it was off the java sun site that they do not make a x64 plug in....any help thanks

---

### Post by taurus on 2009-03-09
[http://java.sun.com/javase/downloads/?intcmp=1281](http://java.sun.com/javase/downloads/?intcmp=1281)

---

### Post by xXNI4NI on 2009-03-09
ty taurus solved

---

