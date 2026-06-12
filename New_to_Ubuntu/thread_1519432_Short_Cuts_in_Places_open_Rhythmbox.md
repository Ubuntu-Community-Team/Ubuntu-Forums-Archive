---
title: "Short Cuts in Places open Rhythmbox"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Grim-Fandango on 2010-06-28
Clicking on the shortcuts in "Places" brings up Rythmbox. I searched the forums and found the exact same problem, unfortunately no one had a solution. Any Ideas? I'm running Lucid on a Dell 1737 and I'm an absolute beginner. The "Places" menu was working fine at one stage but I can't pinpoint when it went awry. 

[http://ubuntuforums.org/showthread.php?t=1324760](http://ubuntuforums.org/showthread.php?t=1324760)

---

### Post by psavva on 2010-06-28
> **Grim-Fandango said:**
> Clicking on the shortcuts in "Places" brings up Rythmbox. I searched the forums and found the exact same problem, unfortunately no one had a solution. Any Ideas? I'm running Lucid on a Dell 1737 and I'm an absolute beginner. The "Places" menu was working fine at one stage but I can't pinpoint when it went awry. 

[http://ubuntuforums.org/showthread.php?t=1324760](http://ubuntuforums.org/showthread.php?t=1324760)

It seems that you have managed to associate folders to open with Rythmbox.  This is fairly easy to fix:

Open terminal and type:
```
nautilus
```
This will bring up the folder browser.

Right Click on Any Folder and click "Open with Other Application"
Choose "File Browser" from the list and youre done :)

This will fix the associate of folders with File Browser instead of Rythmbox.

I also suggest you look at this post:

[Post]("http://ubuntuforums.org/showthread.php?t=51071")

---

### Post by Grim-Fandango on 2010-06-28
> It seems that you have managed to associate folders to open with  Rythmbox.  This is fairly easy to fix:

Open terminal and type:
     Code:
     nautilus 
This will bring up the folder browser.

Right Click on Any Folder and click "Open with Other Application"
Choose "File Browser" from the list and youre done :smile:

This will fix the associate of folders with File Browser instead of  Rythmbox.Perfect! That sorted the problem. Thanks Psavva :p

---

### Post by Jeztastic on 2010-10-07
Hi,

I have the same problem. I have tried the suggested fix several times, and it has not worked. The file association shows as being correct, yet it still only opens with Rhythmbox.

Update: Fixed it with a variation of post#18 in the bugfix:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

Removed ```
rhythmbox.desktop;
``` from line;
```
inode/directory=rhythmbox.desktop;nautilus-folder-handler.desktop;nautilus-browser.desktop;
``` in location ```
home/username/.local/share/applications/mimeapps.list
```

Hope this helps.

---

