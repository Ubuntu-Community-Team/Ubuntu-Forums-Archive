---
title: "asynchronous updating"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by php_penguin on 2009-04-16
Hi,

Sorry to be a PITA to the mods but you probably need to move this into a different forum...

Anyway, I am wondering if there is a reason that the update process waits for all downloads to finish before installing them?

Whilst there are dependancy issues within groups of libraries and such, surely the system could download these groups disrete processes and install them once all dependancies are satisfied?

Just wondering because I am currently doing a 340mb update over a 5-50kb connection, and the sooner these updates install the sooner I can forget about it!

tl;dr: Why does the update manager not install software as it is downloaded?

---

### Post by Hospadar on 2009-04-16
I suspect it is for dependancy reasons and simplicity in general, but, if you have a slow connection and can't necesarily download them all at once, this might ease your mind:

Although packages (And their updates) are not installed as they are downloaded, they get downloaded directly to the package cache (which lives in /var/cache/apt if you are ever curious) and then get installed from there, so once the package manager downloads a package, it will be in the cache, ready to be installed.  When you do another update, it will check the cache before downloading the package again, so you don't have to worry about having to re-download packages if you need to kill the package manager mid-update (although once it's gotten to the point where it's actually installing packages, you should not interrupt it)

---

