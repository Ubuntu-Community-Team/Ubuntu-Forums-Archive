---
title: "fstab mount options"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by Tejus on 2010-12-26
I'm dual booting ubuntu from an ext4 partition and windows 7 on ntfs. I have a couple of other ntfs partitions too.
To mount the other partitions at bootup, i used to add this to my fstab:

/dev/sdxy   /media/whatever  auto    noatime,nodiratime  0,0

This works for me, but i would like to know if i can tinker with it.

Are there any other options i can use, or any that i don't need to use but i'm using right now, etc.

I didn't find much on "diratime" and "nodiratime" on google. is it deprecated or something? What about "noatime"?

Will only one option, the "default" one do?

---

### Post by bodhi.zazen on 2010-12-26
See man mount =)

google:

[http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)

And this:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

