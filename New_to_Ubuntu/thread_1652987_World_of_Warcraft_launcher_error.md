---
title: "World of Warcraft launcher error"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by Mokie on 2010-12-26
I purchased a computer from a non-profit tech shop that reconditions and resells to the community.  It came with Ubuntu 10.4.1 so I am having to learn how to use it.

I am installing WOW (have never played before!) and have been following the instructions here ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)).  I think I did everything okay so far, but when I clicked on the WOW icon on my desktop, the launcher started, then said it encountered a serious problem and needed to close.  I tried to troubleshoot, somewhere it said to look for the wtf.config file, but it's not there. (it said I had to start WOW to get it to create the file, but, if I can't install it, how can I start it???)  I'm really stuck at this point and could use some help figuring out what to do next.  Many of the instructions are terribly confusing to a beginner, ugh. I'm gonna keep trying to get this to work, but sure could use some help. 

[bug #23875 at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549), is this relevant?]

[ran apt-get update and install, don't know if that helped.  Then ran $ wine Repair.exe from within the WOW folder.  Then ran $ wine launcher.exe.  This time the WOW panel opened, started a download updater, then I got this message:  "Blizzard updater failed with an internal error. Contact Blizzard technical support"]

[Tried running $ wine Blizzard update and $ wine launcher.patch.exe from WOW folder, not much.  Then ran $ wine wow.exe and it opened the sign-in page, launched the updater ran me through the accept/decline pages, then said "Patch required" so I clicked ok. It appeared to finish (100% complete) but then it minimized the screen wouldn't let me maximize it again. Had to kill it.Ran wow.exe again, same thing. ]

---

### Post by diablo75 on 2010-12-26
Wish I had more helpful advice, but you might visit this forum instead:

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

It pertains to nothing but Wine.  You should post there; you'll get more replies for this particular issue.

---

### Post by Mokie on 2010-12-28
Thank you. The Wine link was helpful.  I was able to get it going, then decided to load it on my Windows machine instead!  (Better graphics card).

---

