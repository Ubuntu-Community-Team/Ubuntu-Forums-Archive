---
title: "Cannot edit frostwire downloads"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by vivi11191 on 2009-07-24
I have Frostwire on my mac and can download songs with it, but once the songs show up in my library I cannot move them to another playlist or edit them (song info, album artwork). I also have trouble opening Frostwire unless I set it to open at startup.  Any ideas why?? :-(

---

### Post by PGScooter on 2009-07-24
Hi vivi11191,

That sounds pretty frustrating! It must be because of "permissions." Do you know where your downloads are being downloaded (as in, the physical location of the folders) ?
Let's pretend they're in your /home/vivi folder, and that they're named "completed" and "incomplete".
Please post the output of ```
ls -l | grep -i incomplete
``````
ls -l | grep -i completed
```
I bet that the owner and the group will be "root". So you will have to change them:
```
sudo chown vivi completed
``` where "vivi" is your username. The one that is /home/vivi.

also do a ls -l on the files inside the folders and see if they're owned by root. Also, you may have to give yourself read and write permissions.

For some homework, read up on the chmod, chown, and chgrp man pages by typing ```
man chmod
```

---

