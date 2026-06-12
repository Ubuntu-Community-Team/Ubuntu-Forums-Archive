---
title: "Shockwave and Flash in Firefox Ubuntu 10.04"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Sumatie on 2010-04-25
It has taken me many hours of scouring the web to find how to do this. In the end none of the guides I found covered all the points I needed to get this working. Here is how it worked for me:


[LIST=1]
[*]I downloaded the latest flash player for linux from [http://get.adobe.com/flashplayer/?locale=](http://get.adobe.com/flashplayer/?locale=) as an archive.

[*]I extracted the archive into the download folder and found the file libflashplayer.so 

[*]For ease of reference I dropped that file into /home/(your computers name)/.mozilla/plugins

[*]I then needed to go into Firefox's preferences so,

[*]Open firefox, go to, edit, preferences then Applications

[*]Under applications go to Flash Video in the left hand column and in the right column choose - Use Other

[*]From there you will need to navigate to /home/##/.mozilla/plugins and select libflashplayer.so

[*]Reload Firefox and it all should work
[/LIST]


For shockwave this guide worked perfectly.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

I now have fully functional Flash and Shockwave with no issues.

Hope this helps.

---

### Post by k3lt01 on 2010-04-25
Or you can just enable the Canonical Partner repository and install adobe-flashplugin through that!

---

### Post by Sumatie on 2010-04-25
That was my problem. I did that and a host of other steps and nothing worked. This just my work around.

---

### Post by k3lt01 on 2010-04-25
Did you file a bug report? It worked for me everytime so I am wondering if something has happened during the development process.

---

### Post by lovinglinux on 2010-04-25
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

It has instructions for 32bit and 64bit users.

---

### Post by Sumatie on 2010-04-25
Yeh I filed bug reports and follow at least 6 different how-to articles. I really only posted this because this is how it worked for me and I found no instruction on it anywhere else. 

The real problem wasn't ubuntu loading the flash plugin, it did it fine, it was Firefox that failed to identify it. So really I simply showed it exactly where to find the manual way...it works well.

The idea behind downloading off the adobe website is simply to ensure the most current version. Anyhow hope it helps others out there.

---

### Post by moodle on 2010-04-29
Did you do a 

sudo apt-get update

?

That worked for me.

---

### Post by Sumatie on 2010-04-30
Mate I spent many days trying differnet solutions...this one worked...people seem to have issue with simplisty of it. Please all think from a complete linux, even computer noob perspective.

Beginners this works, my firefox has been great since I took these steps. 

All other tutorials failed to get me to this point. This way avoids the need for terminal and using linux repositories which aren't always the most current.

---

### Post by Sealbhach on 2010-04-30
It's a nice simple solution, thanks for sharing it.

.

---

### Post by luissquall on 2010-05-01
This solution worked for me: [http://ubuntuforums.org/showthread.php?t=1467405#post9206658](http://ubuntuforums.org/showthread.php?t=1467405#post9206658)

---

### Post by alcyst on 2010-05-12
Basic Q here, I get the error, but don't see a "Flash Player" in Edit/Pref/Applications, am I mssing something?

---

### Post by livanaros on 2010-06-12
> **lovinglinux said:**
> See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

It has instructions for 32bit and 64bit users.

This one worked for me after removing the conflicting plugins manually. Many thanks!!

---

