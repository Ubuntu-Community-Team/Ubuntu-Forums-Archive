---
title: "Restore automatically deleted tmp files?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by djm227 on 2009-12-11
Is there a way to restore recently automatically removed files from the tmp folder?  The buffer speed of my connection is extremely slow, so I usually let videos download to the tmp folder before watching them...but once and a while (after waiting for over an hour, I might add) I exit the web page by accident before backing up the video, and it gets automatically deleted.

Is there a place to which these automatically deleted tmp files go?  Like a system recycle bin or something?  Any help would be appreciated, as I just wasted about an hour of my life buffering a video, only to lose it.

Thanks.

---

### Post by kerry_s on 2009-12-11
nope, it's gone.

---

### Post by abeisgreat on 2009-12-11
Sorry mate, they're gone. I do that same thing, and it always sucks when you don't mean to click away.

---

### Post by djm227 on 2009-12-11
Well that sucks.  Isn't there a way to turn off automatic delete on that folder?

Again, thanks for the help.

---

### Post by abeisgreat on 2009-12-11
Well I believe it is Firefox auto-deleting them, not the folder, so check your FF settings. I might be wrong about that, feel free to correct me.

---

### Post by ayenack on 2009-12-11
Try This;

```
sudo apt-get install testdisk
```

TestDisk comes with PhotoRec which is very good at recovering media files.

To run PhotoRec.

```
sudo photorec
```

To try to recover the files. Check out cgsecurity for instructions on how to use. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

