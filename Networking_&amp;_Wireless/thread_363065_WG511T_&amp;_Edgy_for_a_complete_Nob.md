---
title: "WG511T &amp; Edgy for a complete Nob"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by kamaboko on 2007-02-16
Hello,

Today this is day 1 for me and Linux.  I've lived in the MS world for over 20 years.  So...today I've installed Ubuntu on a Compaq Presario laptop and do not have WiFi.  I'm using a Netgear WG511T card.  Now I realize that this issue has been solved, but for a complete nob like myself, I have absolutely no idea what the "solution" means.  I don't understand the "lingo" ya guys are speaking.  So, from a complete nob perspective, can some please explain how I do fix this?  How would you explain this to your dad who just sat in front of a computer for the first time in his life.  I think about about sums up my understanding of Linux. LOL. 

Thanks,
K

---

### Post by Floppyjoe on 2007-02-16
From what I understand from this link:
[http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212](http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212)
You need to open up a terminal by clicking on Applications/Accessories/Terminal.
Then you need to issue the following command from the terminal:
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```
This may be all you need to do to get it to work.
If that doesn't work post back here for more help.

---

### Post by kamaboko on 2007-02-16
cool.  thanks for the help

---

