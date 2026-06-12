---
title: "How Do I Remove New Kernel"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by hobo on 2010-01-11
I recently screwed my audio into the ground using 2.6.31-18 and after many tries was unable to get it back. So I reverted to 2.6.31-17 and all is well.

The question is: **[COLOR="black"]How do I remove 2.6.31-18? [/COLOR]**and do I need to edit GRUB before I do?

---

### Post by philinux on 2010-01-11
> **hobo said:**
> I recently screwed my audio into the ground using 2.6.31-18 and after many tries was unable to get it back. So I reverted to 2.6.31-17 and all is well.

The question is: **[COLOR="black"]How do I remove 2.6.31-18? [/COLOR]**and do I need to edit GRUB before I do?

If you're running lucid you need to post here. [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377) Someone may know how to get your audio going.

---

### Post by KIAaze on 2010-01-11
Try:
```
sudo apt-get remove linux-image-2.6.31-18-generic
```

---

### Post by slakkie on 2010-01-11
> **philinux said:**
> If you're running lucid you need to post here. [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377) Someone may know how to get your audio going.

Lucid doesn't have 2.6.31.x something, Lucid is using 2.6.32.x

---

### Post by hobo on 2010-01-11
I am running 9.10 on this image along with GRUB 1.something. Sorry for the confusion and thanks for the quick response.

---

### Post by hobo on 2010-01-11
That cmd did the trick and updated GRUB also. thanks again

---

### Post by slakkie on 2010-01-11
Please mark the thread as solved so others can see it is solved.

---

