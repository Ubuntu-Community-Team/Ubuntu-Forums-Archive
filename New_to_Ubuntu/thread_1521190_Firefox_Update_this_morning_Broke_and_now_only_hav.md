---
title: "Firefox Update this morning Broke and now only have v2.0"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by squid68 on 2010-06-30
Got the following error:

/var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/pixmaps/firefox.png', which is also in package firefox-2 E: /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/bug/firefox/presubj', which is also in package firefox-2.

Says package is Broken and to use Broke Filter to find it. Huh?  The Icon to run Firefox also crashed and now only have v2.0 with no addons, extensions or bookmarks. Please help!!

---

### Post by TeoBigusGeekus on 2010-06-30
Open System-Administration-Synaptic and filter only the broken packages.

---

### Post by lovinglinux on 2010-06-30
Edit: See next post.

---

### Post by chrisccoulson on 2010-06-30
This issue was fixed this afternoon (see [bug 600022]("https://edge.launchpad.net/bugs/600022")). Sorry for the inconvenience

---

### Post by hugo.tyson on 2010-07-01
I found that (before the proper fix) it was fighting with Firefox 2; uninstalling FF2 let it fix itself, just going broken packages, fix wasn't enough on its own.

But now, nothing flash works at all.  The "protection against crashes" is all very well, but it now says "flash crashed" for every single flash object.  Sigh.  Fair's fair this is the first time an ubuntu auto-update has screwed up for me, but I had got used to better.

---

### Post by chrisccoulson on 2010-07-01
> **hugo.tyson said:**
> I found that (before the proper fix) it was fighting with Firefox 2; uninstalling FF2 let it fix itself, just going broken packages, fix wasn't enough on its own.

But now, nothing flash works at all.  The "protection against crashes" is all very well, but it now says "flash crashed" for every single flash object.  Sigh.  Fair's fair this is the first time an ubuntu auto-update has screwed up for me, but I had got used to better.

Several people seem to be reporting a similar issue, but it's not something anybody testing the updates experienced. If your issue is being caused by the new OOPP feature, you can try going to about:config and setting dom.ipc.plugins.enabled.libflashplayer.so to FALSE, and seeing if that works for you.

---

### Post by thgthg on 2010-07-01
Since Firefox update it is impossible to start Firefox. Have tried to uninstal both FF 2 & 3 without success. Trying to start FF says that FF is already running. System 8.04

---

### Post by lovinglinux on 2010-07-01
> **thgthg said:**
> Since Firefox update it is impossible to start Firefox. Have tried to uninstal both FF 2 & 3 without success. Trying to start FF says that FF is already running. System 8.04

First make sure Firefox is not running by killing firefox-bin process.

```
killall firefox-bin
```

Some people reported that deleting **secmod.db** file from your Firefox profile solves the problem.

---

### Post by thgthg on 2010-07-02
Deleteing secmod.db fixed the problem. Now FF is OK again. Thanks!

---

