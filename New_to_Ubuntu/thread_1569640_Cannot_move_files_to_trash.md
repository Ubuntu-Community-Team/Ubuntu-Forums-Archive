---
title: "Cannot move files to trash"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by zawmai on 2010-09-07
Hello fellow Ubuntu users. I need help deleting some files. I recently downloaded a game with its crack. So, after I finished installation. I tried to move the crack folder to trash, but the permission was denied. The folder even has a picture on a lock on it.

Here is the image with the error:

[http://yfrog.com/2oscreenshotuwp](http://yfrog.com/2oscreenshotuwp)

---

### Post by garvinrick4 on 2010-09-07
Hit ALT/F2 then type in 
```
gksudo nautilus
```

Now you can throw away in root. 
Needed root permissions to delete file.

---

### Post by zawmai on 2010-09-07
> **garvinrick4 said:**
> Hit ALT/F2 then type in 
```
gksudo nautilus
```Now you can throw away in root. 
Needed root permissions to delete file.

Thanks, I deleted the folder. I'm not sure how the code works, but it opened up a window with a Desktop picture. Then, I clicked on it but don't see the crack folder to delete. So, I went to home>desktop>Crack and delete it. Is that how it's supposed to work?

---

### Post by mapes12 on 2010-09-07
> Now you can throw away in root.
Needed root permissions to delete file.If you delete stuff using Nautilus with root permission make sure you press and hold down the Shift key at the same time as hitting delete. If you don't all you will do is fill up Roots trash bin without realising it until you run out of disk space. You will then need this:-

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

.............been there and got the T shirt. ):P

---

