---
title: "Update Manager Question"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by WeAreLinux on 2010-10-28
I have a quick question about using the Update Manager.

When upgrading Firefox today, UM displayed FF should be 10MB download size but when viewing the details during the download, it showed FF was actually 11.3MB. I then noticed UM displayed my total upgrade size (Firefox with Gnome branding, etc.) was supposed to be 11.1MB but obviously it was more towards 13MB total.

Is this normal? a known issue? Never really paid attention to the download details until today.

TIA

---

### Post by ubunterooster on 2010-10-28
Remember to add the size of your plugins and bookmarks adding to the install

---

### Post by mcduck on 2010-10-28
Could also be the common case of programs using a different definition for MB (as in 1000kB versus 1024kB).

Or downloaded size versus size when installed (.deb packages are compressed), I can't remember what exact information the Update Manager gives during updates. Too bad there isn't anything to update at the moment so I can't even check that. ;)

---

### Post by WeAreLinux on 2010-10-28
> **mcduck said:**
> Could also be the common case of programs using a different definition for MB (as in 1000B versus 1024B).


I think you're right. Did the math & it adds up. Then again, I'm horrible @ math, so I cant be 100% sure,lol.

If that is the case, it would be nice with everything on Ubuntu calculated with one universal standard to avoid minor confusions.

When checking, Synaptic also reports FF as 11.3MB.

Thanks

---

### Post by AngusH on 2010-10-28
It's difficult to have one universal standard. MiB(1024) generally makes more sense because it is the binary number, but MB(1000) is sometimes better because that's the size that drive makers use (because it makes the drives sound bigger).
Angus

---

