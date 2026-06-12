---
title: "do I have to use X?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by maheshjr2000 on 2009-04-30
Is there an alternative? The latest update to 9.04 just killed my integrated graphics and apparently xorg is at fault.

---

### Post by lykwydchykyn on 2009-04-30
There's not really an alternative, at least not readily available and certainly not one that will give you better results.

Are your graphics intel?  You can revert to the old intel driver, that's what I had to do to get around some weirdness in the new intel driver.

---

### Post by maheshjr2000 on 2009-04-30
Ya but I tried it with 9.04 and it didnt do much. Well I was using Urban Terror and it didnt do anything.

---

### Post by Sef on 2009-04-30
From the [release notes]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Switching%20to%20ext4%20requires%20manually%20updating%20grub"):

> **Performance regressions on Intel graphics cards**

 Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases ([252094]("https://bugs.launchpad.net/bugs/252094")).  Many of the issues have been resolved in Ubuntu 9.04, but some remain. 

[LIST]
[*]Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
[*]Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our [testing]("https://wiki.ubuntu.com/X/UxaTesting") has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf.  Users wishing to maximize stability should stay with the standard default acceleration method, "EXA". 
[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/alert.png[/IMG] In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
[*]If none of the above helps, some users reported success with [using an older driver version]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").
[/LIST]
 
**Display freezes with Intel graphics cards**

 Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see [339091]("https://bugs.launchpad.net/bugs/339091")). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.   
If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes. 
These freezes happen particularly often on the i965 chips ([359392]("https://bugs.launchpad.net/bugs/359392")). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

---

### Post by maheshjr2000 on 2009-04-30
Sef I know. Ive tried ALL of the remedies presented and NONE have worked except for UXA and UXA crashed my system in 5 minutes.

---

