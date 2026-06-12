---
title: "firefox flash problems"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by TooCrooked on 2009-10-29
hi,

browsing the intarwebs, i came on a site that required flash. firefox prompted me to install adobe and some other flash plugin. so i did.

the video from this site played fine. hungering for more, i went to break.com. the video did not show up properly. instead, i got the attached picture.

i went to youtube. the videos play, but they're way out of sync.

so... i wanted to uninstall firefox. i assumed EVERYTHING would go with it. i uninstalled the firefox package. firefox still ran. i uninstalled the ubufox package (note: both were complete removals). ubufox uninstallation resulted in no more firefox.

i reinstalled firefox and the various dependancies. when i started up, firefox happily was configured just as it was when i left. everything was still **** broken.

how do i uninstall firefox so that everything about it goes away and i start from ground zero with no plugins or previous settings? even my damn customized toolbar remained despite my "de-installation"

---

### Post by mapes12 on 2009-10-29
Firefox is not the problem. It's the Flash Plugin you have installed. Have a look here: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

and here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by TooCrooked on 2009-10-29
fair enough, but why doesnt the uninstall even affect the configuration of firefox? assuming i was having some other problem that i felt that a reinstallation would fix, how would i uninstall firefox so that it would blow away all previous configuration information???

---

### Post by lovinglinux on 2009-10-29
> **TooCrooked said:**
> fair enough, but why doesnt the uninstall even affect the configuration of firefox? assuming i was having some other problem that i felt that a reinstallation would fix, how would i uninstall firefox so that it would blow away all previous configuration information???

Because that's how it works. Firefox creates user profiles, so you can keep your settings between upgrades, easily backup them and migrate to other computers. Users that have a separate home partition can even re-install Ubuntu while keeping their applications settings intact. This is not an issue, is a benefit.

Also imagine if re-installing Firefox would remove all settings and your machine is shared by 10 users. What would you do if you need to re-install Firefox due to some file corruption? 

Anyway, to reset your settings, close Firefox and delete ~/.mozilla/firefox folder or start the Firefox Profile Manager (see command below) and delete the profile from there:

```
firefox -P
```

---

