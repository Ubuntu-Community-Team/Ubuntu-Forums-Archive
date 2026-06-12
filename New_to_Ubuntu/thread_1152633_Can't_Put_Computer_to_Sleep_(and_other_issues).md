---
title: "Can't Put Computer to Sleep (and other issues)"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Polyethylene Paul on 2009-05-08
My brother decided to take the hard drive from his old computer and boot my computer from it. I only have one SATA controller, so he unplugged it. When I booted Ubuntu 9.04 off my hard drive again it checked the disk. Now a few things don't work:


[LIST=1]
[*] indexer Files become corrupted soon after starting the re-index,(Re-Index is necessary because they became corrupted in the first place)
[*]the Weather Report Panel Application fails to retrieve information,
[*]the computer is no longer able to sleep (I tried it once after booting from my hard drive again; it shut down and when I rebooted it said something along the lines of Sleep failed. Now the option isn't even present)
[/LIST]
Please Help.  Thanks in advance

---

### Post by Didius Falco on 2009-05-08
> **Polyethylene Paul said:**
> My brother decided to take the hard drive from his old computer and boot my computer from it. I only have one SATA controller, so he unplugged it. When I booted Ubuntu 9.04 off my hard drive again it checked the disk. Now a few things don't work:


[LIST=1]
[*] indexer Files become corrupted soon after starting the re-index,(Re-Index is necessary because they became corrupted in the first place)
[*]the Weather Report Panel Application fails to retrieve information,
[*]the computer is no longer able to sleep (I tried it once after booting from my hard drive again; it shut down and when I rebooted it said something along the lines of Sleep failed. Now the option isn't even present)
[/LIST]
Please Help.  Thanks in advance

For 1. From the Release Notes:
> 
**Tracker index corruption**

  In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. As a workaround, please press Alt+F2 and run tracker-processes -r. This will be fixed in a post-release update soon

2. I do wonder if this could be because of Tracker sucking up so many resources. TRy the Tracker indexing fix and see if that corrects it. If not, we can do some more digging.

Can't really help with three but I'll do a few searches and see what I can find.


Regards,

Didius

---

### Post by mprince on 2009-05-08
> 2. the Weather Report Panel Application fails to retrieve information,

Remove your old location and create a new location and see if that helps fix the weather data.

---

### Post by Polyethylene Paul on 2009-05-21
Indexer is back up and working, but I still can't sleep the computer or use the weather applet.

---

### Post by Polyethylene Paul on 2009-06-21
The computer can now sleep and the weather-applet works. I believe recent updates have fixed the issues.

---

