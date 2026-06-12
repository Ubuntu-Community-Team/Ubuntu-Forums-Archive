---
title: "Grub Stage 1.5 Error 25"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by eric.rost on 2009-04-02
I coincidentally recreated this "Classic" user's error while installing Hardy on a friends OLD box:

[http://ubuntuforums.org/showthread.php?t=122473](http://ubuntuforums.org/showthread.php?t=122473)

The Grub Stage 1.5 Error 25 will occur when you install your MBR on a drive other than the primary drive and the BIOS battery is dead because the BIOS will not remember the IDE bus mapping to the drives and will only detect the Master drive on the Primary bus. Without changing anything written to disk, replace the battery and everything will work.

This error is not Breezy, Hardy, or any other version specific and hopefully this will help some other helpless newbie from making an *** of themselves for two years on slashdot.

[http://slashdot.org/~UbuntuDupe/](http://slashdot.org/~UbuntuDupe/)

---

