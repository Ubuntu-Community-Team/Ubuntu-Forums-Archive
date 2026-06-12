---
title: "Any suggestions for maximum performance for a clean install?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Jotamide on 2010-07-16
Hi,

I recently installed ubuntu and my other OS is win 7, I have both in dual-boot mode with no problems.
Since I have some free time this weekend and I wanted to format my pc to get rid of some garbage in win 7 and change the amount of space I first gave ubuntu on the partition. I was wondering what would be the best method to install both OS and get the best out of them.
From what I read apparently is better to install ubuntu after win 7 to not have troubles with GRUB, and also that if you create a "shared partition" is possible to share bookmarks and plugins in firefox for both OS. What other stuf do you recomend?

Thanks

---

### Post by Jotamide on 2010-07-16
:popcorn:

---

### Post by potat on 2010-07-16
This isn't really a performance issue, but some people like to put /home on a separate (big) partition, and leave everything else on a smaller partition. This lets you reinstall the OS without disturbing any of your files/settings.

How to do it on an existing install:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

As for bookmark syncing, it might be easier to use the new Weave plugin ([https://addons.mozilla.org/en-US/firefox/addon/10868/](https://addons.mozilla.org/en-US/firefox/addon/10868/)). But if you want a shared partition, make sure to make it FAT32 (or NTFS) so that Windoze can use it.

As for performance, you can reduce some of the bloat by switching to a lighter WM (try Xfce first).

Have fun!

---

### Post by Jotamide on 2010-07-21
Thanks for the advice, but I have one last question.

Is it better to do the partitions with gparted or the windows tool?

---

### Post by philinux on 2010-07-21
> **Jotamide said:**
> Thanks for the advice, but I have one last question.

Is it better to do the partitions with gparted or the windows tool?

For win 7 use it's tool to shrink win partition. Do not use linux for this. After that you can use gparted or the installer to play with the ubuntu partitions.

---

### Post by Paqman on 2010-07-21
Install preload, it's a very smart adaptive pre-caching tool that works quietly in the background monitoring what apps you actually use, and preloading them into memory so they're ready for you when you want them.

It takes a week or two to learn your habits, so you won't see any immediate improvement.

Also, turn off any stuff you won't use, like Assistive Technologies or Bluetooth if you don't have any Bluetooth hardware. Go to System > Prefs > Startup Applications and see what's in there.

---

### Post by mike555 on 2010-07-21
you might want to check this out, if your low on installed memory ...
[http://ubuntuforums.org/showthread.php?t=1535067](http://ubuntuforums.org/showthread.php?t=1535067)

---

### Post by oldfred on 2010-07-21
If you are going to be in both windows & Ubuntu you will need the shared NTFS partition.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
older version:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

---

### Post by Jotamide on 2010-07-26
Thanks everyone! Now I'll read everything to do the installations as smoothly as possible.

---

