---
title: "Running Counter-strike:source through Wine"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Goldline on 2009-11-13
hello all,

Im running CS:S through the latest wine version 1.1.3.2.
But the text appears as very small hard to read through is 
there a way that i can change that?

some screenshots below:

[IMG]http://31mjaa.bay.livefilestore.com/y1pRwjG0-rJsHPRNVsQM4dCqlaKDt5d9atWSGm7fDoBZs48M7dJqZ3Jrl6gcJ1irrdRYuE69-dir_TcQUsTOVel9ZB3wp6fAwkL/serverlist.png[/IMG]

[IMG]http://31mjaa.bay.livefilestore.com/y1pYbBDHDbPV10eKI0urSJzfVof-25u-0vGTwbXe50uq5Tu-jz5ex3YPj3YIan77KBD_Rr8h6eHegpy3_4RYD52BvXW5qu9UeV3/console.png[/IMG]

---

### Post by Paqman on 2009-11-13
The Wine App DB is a good place to find out about running Windows apps on Wine. Check the [Counter Strike Source]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731") entry for more info.

---

### Post by XCan on 2009-11-13
That looks like you're missing the ms fonts. I would try and install the corefonts through winetricks [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) . Be aware though, that it may potentially change the rest of your fonts on your system to ms fonts.

---

### Post by proxess on 2009-11-13
You can install the package msttcorefonts or something similar.

Ubuntu-restricted-extras should do the trick.

---

### Post by Goldline on 2009-11-13
Ive installed the package MScorefonts -/- ubuntu-restricted-access aswell, not working.

---

### Post by LowSky on 2009-11-13
[QUOTE=http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731]**Lacking fonts.** You need Tahoma and Lucida Console fonts for every text to show properly. Use winetricks to get them if you don't have a windows install handy.[/QUOTE]

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

