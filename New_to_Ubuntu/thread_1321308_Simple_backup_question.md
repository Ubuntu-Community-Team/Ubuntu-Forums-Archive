---
title: "Simple backup question"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by ed-koala on 2009-11-09
If I have separate root and home partitions, if I copy the contents of /home somewhere, upgrade and copy the files back, will things like wine and Wow be back without reinstalling?  I know things like my music files will be fine, but do packages installed previously migrate back when you copy all of home back?

---

### Post by Tman5293 on 2009-11-10
Nope. Sorry. Your gonna have to reinstall them. If you don't mind me asking, why do you have separate partitions for your home and root directories?

---

### Post by ed-koala on 2009-11-10
Just old advice I saw stating its easier to have home on a separate partition.  Thanks for the info, mostly I'm worried about my world of warcraft data/game files, which are easy to copy/restore. Wondered how far a clean install would make me go in restoring programs is all ... now I know.

---

### Post by rossmoore on 2009-11-10
I also have home on a separate partition. It means that, if I'm careful, I can install a new system and not have to move my music and pictures around.

You'll have to install the software again, but any configuration will be stored in your home directory. So themes and compiz and whatever can be instantly back to how you configured them - once you've installed the software again, and provided the config setup hasn't changed...

I'm not convinced this is the best setup though - I think I prefer replacing the Music sub-directory in home with a symlink to a "data" partition that has pictures, music, videos, whatever on there. Or, if you have the money/setup, put all that on a separate drive rather than a separate partition.

---

