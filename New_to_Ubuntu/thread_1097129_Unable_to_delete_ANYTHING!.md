---
title: "Unable to delete ANYTHING!"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by klaxor on 2009-03-15
Recently, I have been completely unable to delete any file whatsoever, including files that were already in the recycle bin.  The computer has been treating everything as though it were Read-only, which of course, nothing is.

I am completely perplexed as to how this could have happened.  Up until yesterday, I had deleted files left and right with no problems!  But out of no where, after an update download for Wine and an attempt at downloading a torrent, my computer has begun this strange behavior.

Any advice???

---

### Post by klaxor on 2009-03-15
It seems almost as though I don't have the permission...

---

### Post by taurus on 2009-03-15
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~
ls -la ~/.local/share/Trash/files
```

---

### Post by SuperSonic4 on 2009-03-15
Have you checked the owner of the files you want to delete? Root can delete anything but use it with care

---

### Post by S.A.A on 2009-03-15
Open terminal and type:
sudo rm <your file name>

---

### Post by Yashiro on 2009-03-15
Can you create a text file on your desktop?

---

### Post by SuperSonic4 on 2009-03-15
> **S.A.A said:**
> Open terminal and type:
sudo rm <your file name>

```
gksu nautilus
``` will open nautilus as root then you can navigate to your files

---

### Post by geezerone on 2009-03-15
What error message do you get exactly when trying to empty the trash?

---

### Post by klaxor on 2009-03-16
Problem solved!  Thanks guys!

(Honestly, I don't know how I did it, but your advice helped!)

---

