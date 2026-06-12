---
title: "Runes of Magic not opening"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by jeffymarts on 2010-01-03
Hi. I'm using PlayOnLinux to play Runes of Magic, it installed just fine. It took forever to download all the updates and patches, but that's to expect from a game that has released for a while, especially an MMORPG. However, when clicking on the link for the game now nothing happens. There is a link under the Wine menu called "Runes of Magic on the Web", which doesn't work. Another link under Other, called simply Runes of Magic, also not working. There is also a link located in PlayOnLinux that doesn't work either (Highlighted it and clicked run). Help please.

---

### Post by jimreynold2nd on 2010-01-04
install the new wine:
```
sudo apt-get install wine1.2
```
then try again :D
If that doesn't work, try renoving the .wine directory in your home directory (backup first!), then install RoM again.

According to other people, RoM is supposed to work flawlessly under new wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8157](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8157)

Hope this works

---

