---
title: "Andy"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by andystewart on 2009-05-08
why cant i put files on my 2nd hard drive  when i try it says you r not the owner what does this mean ? :confused:

---

### Post by Steven_S on 2009-05-08
I'm an absolute beginner myself, but I'm pretty sure this has to do with permissions. Try searching for that, I'm sure you'll find something!

Also, I saw that you have a similar question already here: [http://ubuntuforums.org/showthread.php?t=1151652](http://ubuntuforums.org/showthread.php?t=1151652)

If you post, be sure to set the option to get e-mailed when a reply comes in. That way, you can re-post to the people trying to help. I'm sure scheuri could help you further if you answer his return questions. 

Might I also suggest that you choose post titles that are a bit more descriptive? Makes it a lot easier to search ;)

---

### Post by Peter09 on 2009-05-08
How are you mounting your hard drive? I believe windows drives are mounter read-only by default.

---

### Post by MysticalRiotCandy on 2009-05-08
You should try ntfsfix ($ sudo apt-get install ntfsfix) and run that on the drive.  Additionally, you'll need to run that on any NTFS drive if you incorrectly shut down Windows when it had mounted it.

---

### Post by pastalavista on 2009-05-08
alt-f2... type gksu nautilus... full permissions file browser. if it's read only, right-click the file folder (mount point probably in /media) select properties > permissions... change owner to you and change to read/write and create/delete

---

