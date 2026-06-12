---
title: "Firefox slows and have to Hard Reboot Sys"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by ninedragons1pearl on 2009-07-21
Ran Firefox 3.0 at first started locking up after screen went gray, tried the upgrade to 3.5 same thing. Created another profile and ran in safe mode, eventually the same result. Tried another Browser without Flash load, same thing. The only thing I could do is boot into stupid xp to post this msg. i dont know what is causing the HD get pegged and sys to lock up at this point.
Tried...
sudo apt-get purge firefox
sudo apt-get install firefox
But Firefox didnt seem to be effected because my bookmarks remained untouched.:confused:

---

### Post by Arup on 2009-07-21
Try alternate like Opera, you can also give Opera 10 beta a try, its quite stable and runs fast. Have you loaded your video drivers btw?

---

### Post by hyperdude111 on 2009-07-21
Could be a RAM issue.

---

### Post by saj0577 on 2009-07-21
> **ninedragons1pearl said:**
> Ran Firefox 3.0 at first started locking up after screen went gray, tried the upgrade to 3.5 same thing. Created another profile and ran in safe mode, eventually the same result. Tried another Browser without Flash load, same thing. The only thing I could do is boot into stupid xp to post this msg. i dont know what is causing the HD get pegged and sys to lock up at this point.
Tried...
sudo apt-get purge firefox
sudo apt-get install firefox
But Firefox didnt seem to be effected because my bookmarks remained untouched.:confused:


I upgraded a few days back and now mine can only handle a couple of tabs whereas before i had 30+ tabs. Best advice is try another web browser and wait for an update. It sure is annoying but thats the best at the minute, just know your not alone,far from it, never understand why they bring out releases with such bad flaws.

Saj

---

### Post by philinux on 2009-07-21
> **ninedragons1pearl said:**
> Ran Firefox 3.0 at first started locking up after screen went gray, tried the upgrade to 3.5 same thing. Created another profile and ran in safe mode, eventually the same result. Tried another Browser without Flash load, same thing. The only thing I could do is boot into stupid xp to post this msg. i dont know what is causing the HD get pegged and sys to lock up at this point.
Tried...
sudo apt-get purge firefox
sudo apt-get install firefox
But Firefox didnt seem to be effected because my bookmarks remained untouched.:confused:

Turn off compiz if it's on.
Dont hard reboot. Alternatives.
1. REISUB [http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

2. Alt+SysRq+k = kills x so you can login again.

---

### Post by lovinglinux on 2009-07-21
Re-installing doesn't delete your bookmarks or any other settings, since profiles are stored in ~/.mozilla/firefox.

I recommend the tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567), but the reports about Firefox greying out are increasing since last week. 

I've "fixed" this on a low-end notebook by disabling Remote Desktop, removing pulseaudio and installing Swiftweasel optimized for the notebook processor.

---

### Post by ninedragons1pearl on 2009-07-21
Thanks a bunch for the nfo....I will try the suggestions you've posted. You all are a wonderful help!:KS

---

