---
title: "Items in trash won't delete"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-02-21
I screwed up Thunderbird a couple of times and had to delete it
and start over.
Those items are now in the Trash and I can't delete them because 
of permission problems. I'm very afraid of using "SUDO" anymore
as I wiped out Ubuntu using SUDO to change permissions for /usr/local/src.
What should I do, please.
Thanks for any help.

2% Ubuntu working on 3%

---

### Post by gymophett on 2009-02-21
I also am having a problem with this. I have a 2gb file in my trashcan, it has a lock on it and won't let me delete it? How can I?

---

### Post by drs305 on 2009-02-21
Take a look at the tutorial with the link to Trash in my signature line. Most likely you have some trash owned by root in your trash bin.

The short answer, start up nautilus with admin powers (gksudo nautilus), navigate to the Trash bin and delete the items or the entire Trash folder using SHIFT-DEL. **Warning:** Be careful what you delete. You can remove system files if you aren't careful and there is no recovery from a SHIFT-DEL operation.

---

### Post by smo0th on 2009-02-21
hi, maybe some script changed your files ownership to root, go to the terminal and type 
```

sudo chown -hR youruser .local/share/Trash/ 

```

this will change all your Trash files ownership to your current user and you'll be able to empty your trash

---

### Post by Jack Shankle on 2009-02-21
Found answer on this forum under "trash permission problem".
It solved my problem.
Thanks

---

### Post by handy on 2009-02-21
There are a few different ways of handling the problem mentioned in this thread:

*_[http://ubuntuforums.org/showthread.php?t=217258](http://ubuntuforums.org/showthread.php?t=217258)_*

---

