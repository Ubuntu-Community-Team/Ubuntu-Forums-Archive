---
title: "config not writable messages"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by TooRight on 2010-05-31
I upgraded to Lucid a couple of weeks back and ever since then I have been getting all kinds of errors about different files not being writable(with config in part of the location name), it seems to happen alot when I have konqquror open, along with showing the contents of that folder as not containing anything when just a few moments before I had been accessing files in that same folder. As well, it seems like my entire harddrive is not writable as I am unable to save anything to disk... I reallyyy need to download some thing for work, so I'm hoping one of you out there will have some idea on what  could be the problem and how to fix it?

---

### Post by nhasian on 2010-05-31
okay we gotta backup here and take this one step at a time.  first of all, you will need to boot from an Ubuntu 10.04 LiveCD or thumbdrive.

go to system-> administration-> disk utility and check the status of your hard disk.  make sure its healthy and that is passes all the diagnostic and smart tests.

then go to system-> administration-> gparted.  select your disk drive and make sure the partitions are not mounted.  then right click on the partition and choose check to have the filesystem checked.

if BOTH of the above turn up no errors then you probably have a permission problem.  you can verify this by downloading whatever it is you need to download to your hard disk from the live cd.

---

