---
title: "Wine :-("
date: 2009-03-09
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-03-09
Hi guys!

I'm a total newbie in Ubuntu - this is my third day using it. It's mostly awesome, but some things I can't get to work. One is Wine.

Yesterday, I started experimenting with it:

- installed Wine from Synaptics, then it appeared in my Applications and I could customize it and everything

Then I tried to install PhotoScape 3.3, one of my favourite programs ever. I could install it, but it wouldn't run. So I uninstalled everything again, thinking I might have done something wrong in Wine to begin with. During today, I found out about Wine-Doors, which sounded pretty cool, so I installed that and found out that it only has very old versions of many programs available (e.g. IrfanView 4, which is like 2 years old).

Anyway, Wine-Doors installed Wine along with itself, but I couldn't use Wine independently of it anymore except when right-clicking on a Windows App and selecting "Open with Wine".

Then, after a restart, for no apparent reason, the "Run with Wine" option disappeared. I uninstalled both Wine and Wine-Doors again, also the orphaned packages etc, re-installed Wine, but I still cannot use it.

Currently, Wine is neither present in my Applicatinos menu nor can I run it from the context menu. Help! Does anybody know how to get it back?

And once I have it back, do you have any idea how to make Photoscape run? Am I missing special DLLs or something?

Thanks!

---

### Post by Kareeser on 2009-03-10
```
sudo apt-get remove wine
sudo apt-get install wine
```

According to the AppDB, Photoscape 3.1 is rated Silver, which means it might only work with DLL overrides or other tweaks first.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13056](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13056)

---

### Post by The Bright Side on 2009-03-13
I re-installed Wine, even uninstalled everything that pertained to it before, but it still won't appear in the context menu :-( What the hell? Is there any way I can get it back there? It's in my APplications, I can configure it and everything, but it's still useless because I cannot run jackshit with it. Any ideas?

---

