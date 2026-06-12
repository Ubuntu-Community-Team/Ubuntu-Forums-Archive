---
title: "problem running fsck"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-07
Hello


sudo fsck
/dev/sdal is mounted
Running e2fsck on a mounted filesystem may cause severe filesystem damage
I have no idea how to fix this problem.Thanks

---

### Post by openuniverse on 2009-12-07
.

---

### Post by diablo75 on 2009-12-07
You can also do this:

```
sudo touch /forcefsck
```

That will force a fsck on your root directory after you reboot.  If you have multiple partitions (such as a seperate partition for your home directory) you'll want to do that same command for it with the respective path modified.  If you don't know what that means, then the above command should be all you need to do.

---

### Post by manny43 on 2009-12-07
how do you umount /dev/sdaI while booting livecd being new to UBUNTU?

---

### Post by 5nak3 on 2009-12-07
It is my understanding that if you boot from the cd the hard drive is not mounted. And in turn you can run your fsck without fear because the disk is not mounted.

So simply insert the livecd, and then run the fsck from you terminal once the livecd has loaded.

---

