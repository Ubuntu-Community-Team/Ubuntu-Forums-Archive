---
title: "Reinstalling Ubuntu whilst keeping programs and data?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by gazz1982 on 2010-06-16
I have had a problem with my desktop, something to do with startx as it freezes, so for the past few months I have been working remotely using a windows machine! I have come to the end of my research and about to start my next project so I would really like to solve this problem. Therefore I want to do a fresh install.

I have many programs installed which I need and many dependencies exist I had to install a few packages but I cant remember what they were, it was last year. Therefore I want to backup my system so it can be restored. Then do a fresh install whilst keeping my data and programs, is this possible? How would I do it, I am worried about losing programs which took me a while to get to work!

Thanks

Gary

---

### Post by mapes12 on 2010-06-16
This shouldn't be difficult:-

- The first thing I would do is make sure /home is on its own partition. This will ensure all your personal settings (wallpaper, FF add ons and the like) are preserved. Here's a HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

- Then backup your applications and dependencies with aptoncd: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

- Reinstall Ubu but select the "Manual" option when the partitioner starts and make sure only / is formatted.

Mark

---

