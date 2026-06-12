---
title: "Video conversion from wmv for KDenlive"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by MisFitt on 2009-11-29
Hi,
I'm using Jaunty.
I'm having problems with KDenlive crashing and I can't capture from the mini dv in kdenlive,it's not even recognising my camera,a Sony.
I resorted to capturing in windows XP movie maker in the hope I could bring the files back to kDenlive but need help converting them from wmv to an acceptable format.
I'm frustrated and have 9 hours worth of tape to sift through so any advice would be gratefully received so i can get on with it.
Thanks heaps.
I posted here as a beginner-should I post in the video/multimedia section instead?Just a thought,cheers
PS-I did have a conversion program for windows but I LOST IT!

---

### Post by scorp123 on 2009-11-29
> **MisFitt said:**
>  I'm having problems with KDenlive crashing and I can't capture from the mini dv in kdenlive,it's not even recognising my camera  You have to install the kernel modules. It's easy, you just need to edit a few files.

Read here:
[http://ubuntuforums.org/showpost.php?p=3831001&postcount=19](http://ubuntuforums.org/showpost.php?p=3831001&postcount=19)

After those modifications any camera with a DV interface should work as capture device.

---

### Post by MisFitt on 2009-11-29
> **scorp123 said:**
> You have to install the kernel modules. It's easy, you just need to edit a few files.

Read here:
[http://ubuntuforums.org/showpost.php?p=3831001&postcount=19](http://ubuntuforums.org/showpost.php?p=3831001&postcount=19)

After those modifications any camera with a DV interface should work as capture device.
OK,thanks very much but I'm a little lost as to where and how those lines need to be entered-sorry

---

### Post by scorp123 on 2009-11-29
> **MisFitt said:**
> OK,thanks very much but I'm a little lost as to where and how those lines need to be entered-sorry The ***where*** is mentioned in that posting. As for ***how***:
```
gksudo gedit /etc/modules
```

After a reboot the modules should now always be loaded automatically.

---

### Post by MisFitt on 2009-11-29
Thankyou so much-done!
sorry about my scrambled attempt at explaining my needs-my head was hurting!

---

