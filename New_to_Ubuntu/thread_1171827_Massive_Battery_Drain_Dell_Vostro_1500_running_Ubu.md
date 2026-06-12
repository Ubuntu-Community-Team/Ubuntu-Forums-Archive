---
title: "Massive Battery Drain Dell Vostro 1500 running Ubuntu 9.04"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by jbcollins on 2009-05-27
My Dell Vostro 1500 is a year old and was running Win XP 2 GB RAM. Switched to Ubuntu 9.04 recently and find that my battery is draining fast in about 30 minutes. On XP, Win 7 and even the previous version of Ubuntu I had for a few weeks - the battery life was close to 1.5 hrs when playing a DVD. Now, without DVD playing battery gets to critical level in 25 - 30 mins. 

I saw some Gurus asking people to run a "TOP" command. Attached is my screenshot of TOP results:

Thanks for your help.

---

### Post by blueridgedog on 2009-05-27
You may want to look at this thread, as it is more or less working through your issue:

[http://ubuntuforums.org/showthread.php?t=1129135](http://ubuntuforums.org/showthread.php?t=1129135)

---

### Post by jbcollins on 2009-05-28
Thanks blueridgedog for pointing me in the right direction. I may have a combination of problems - described [**_here_**]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance"). I reverted my Xorg intel driver to 2.4 as described [**_here_**]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

Noticeable difference in battery drain.

Hope this helps somebody.

---

### Post by blueridgedog on 2009-05-28
Well done.  I have followed the 9.04 issues, hoping that a resolution appears for laptop users.  Perhaps one will come with the next kernel release and new graphics drivers.

---

### Post by blueridgedog on 2009-05-30
This post:

[http://ubuntuforums.org/showpost.php?p=7362567&postcount=58](http://ubuntuforums.org/showpost.php?p=7362567&postcount=58)

In the thread I sent before has a good tip as well.

---

### Post by jbcollins on 2009-05-30
> **blueridgedog said:**
> This post:

[http://ubuntuforums.org/showpost.php?p=7362567&postcount=58](http://ubuntuforums.org/showpost.php?p=7362567&postcount=58)

In the thread I sent before has a good tip as well.

Thanks, I just did that and put my laptop on "Powersave" mode. I'm sure this will be useful. Thanks again.:)

---

