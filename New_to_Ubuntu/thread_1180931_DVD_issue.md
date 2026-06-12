---
title: "DVD issue"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by TheBootstrapKid on 2009-06-07
When i try to play a dvd in jaunty i get an error stating i might not have permission to open the file.

happens in both totem and vlc

---

### Post by SuperSonic4 on 2009-06-07
Have you installed libdvdcss2 from the medibuntu repo?

---

### Post by TheBootstrapKid on 2009-06-07
i tried that.  now i don't get the error message, but when i try to play a dvd nothing happens.

---

### Post by philinux on 2009-06-07
Install the ubuntu-restricted-extras package. Click the link in my sig.

---

### Post by TheBootstrapKid on 2009-06-07
already have it.  still no luck.

---

### Post by albinootje on 2009-06-07
> **TheBootstrapKid said:**
> When i try to play a dvd in jaunty i get an error stating i might not have permission to open the file.

Is this also happening with other dvds ? 

And is this a custom made data dvd (with e.g. you personal backup files on it) or some video dvd from a shop ?

---

### Post by albinootje on 2009-06-07
And is your user in the group "cdrom" ? Check with the command :
```

groups

```

See also here :
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550)
[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/342890](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/342890)

---

### Post by eMJayy on 2009-06-07
This is actually a known bug that occasionally pops up from time to time. Apparently, using certain DVD recorders to make DVD copies can cause errors on the disc that interfere with how permissions are assigned to files on the disc. The only way to play the affected discs is to run them with root permissions. 

This is a link to the bug thread for this issue at launchpad - [here]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550")

---

