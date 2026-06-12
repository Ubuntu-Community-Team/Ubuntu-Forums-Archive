---
title: "File recovery from unmounting partition?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by michaelvolver on 2009-10-31
I have a problem. I tried to install ubuntu on a new partition with Windows Vista on my wife's laptop. I was able to access her files from the boot disk trial, but after installing ubuntu on its own partition I can not access her personal documents, etc from the Windows partition. I did not know when I started that I was supposed to decrease the Vista partition size in Vista before partitioning--I need to recover my wife's files (yes, I did not back them up as I should have). Is there a way to recover her personal files? or view them? (I can see all the windows and program files, but the personal files are not to be found). What did I do wrong and how can I fix it? I am panicing here.

thankyou

---

### Post by jrrader on 2009-10-31
It could be that the files were not moved properly and have been corrupted.   NTFS gets fragmented and I'm guessing you didn't defrag before you resized.  It's always best to use the OS that owns the partition to resize it and no one does NTFS better than Microsoft, since it's their file system.

Anyway, install ntfs-config in Ubuntu.  Run it and it will allow you to mount the Vista parition (also giving your ownership of the drive).  If the files are still readable, this should do it.

---

### Post by michaelvolver on 2009-11-01
Thank you. I will give it a try.

---

### Post by Mark Phelps on 2009-11-01
With the awesome power of Linux utilities comes the risk of destroying things you didn't intend to harm.

The lesson here is to NOT use Linux utilities to mess with MS Windows Vista OS partitions and, more important, to check in these forums to see if there are problems doing something -- BEFORE you go blindly charging ahead and doing it.

---

### Post by UltimaCyberman on 2009-12-24
I use MultiStage Recovery each time I need to recovery data. This [ data recovery tool](http://multistagerecovery.com/) is quite powerful, reliable and isn't expensive. 
So I Recommend it if you need easy-to-use data recovery tool.

---

