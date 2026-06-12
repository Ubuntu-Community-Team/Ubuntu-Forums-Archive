---
title: "Live Disc cloning"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2010-05-07
Hi guys I have a windows disc I need to clone. Are there any linux programs that will do the job well, that I can run from a live CD. I've never used any disc cloning software before.

---

### Post by squaregoldfish on 2010-05-07
The dd command will do what you want - it copies bytes off disks, so it doesn't care about OSs, partitions or anything else - it just copies the raw bytes.

I strongly recommend you read up on the subject before messing with the command though. There's a good discussion of it here:
[URL="http://serverfault.com/questions/4906/using-dd-for-disk-cloning"]
http://serverfault.com/questions/4906/using-dd-for-disk-cloning[/URL]

HTH
Steve.

---

### Post by auburn on 2010-05-07
I think what you're looking for is Clonezilla Live.
It's a live linux cd (boot from this cd on the machine you want to clone). You do not install anything and the menus will mostly select by default the best options for you. I consider it to be *very* reliable, but I've used it enough to be aware it does fail sometimes. I also feel that since the consequences of making a mistake while cloning or restoring can have such dire results (losing all your data) that this is an advanced topic. You especially need to be very aware of the destination and source of what you're restoring/saving. Don't mix them up!! 

This site has a step-by-step screenshots:
[http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla](http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla)

and this site has videos:
[http://www.ilovefreesoftware.com/16/videos/video-tutorial-how-to-clone-disks-using-clonezilla.html](http://www.ilovefreesoftware.com/16/videos/video-tutorial-how-to-clone-disks-using-clonezilla.html)

---

