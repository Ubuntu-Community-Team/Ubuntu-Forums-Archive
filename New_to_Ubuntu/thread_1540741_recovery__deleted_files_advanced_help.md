---
title: "recovery  deleted files advanced help"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-28
dont know if this is possible but should be. i recently had to reformat a partition and of course i lost all the file there. there was on file my wife's seizure log that i need to try to recover. usually unless you thread a file they are still on your hard drive. i know with windows they either overrite them with x and o's of just drop off part of the name to make it unreadable. first can files still be found and second what is a good program. maybe one that you have used if it is not free fine. but free would be a good one to try first/tks in advanced. (note this is an .odt file)

---

### Post by Deiz on 2010-07-28
Yes, you can recover files. But stop writing to the drive immediately, or you risk losing them. Simply put, a regular deletion merely removes references to data. The data is still there, but the space has been freed by the OS - This means that if you were to download some files, they would overwrite the previously-used space, rendering the old files irretrievable.

You might try [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec"), it's known to recognize OpenOffice files.

They have a guide to using it on their site.

---

### Post by aeiah on 2010-07-28
i recommend photorec too. if you have the storage space available, do a dd copy of the drive and try to recover from that rather than the drive its self.

---

### Post by da burger on 2010-07-28
Here is a nice step by step walk through on using photorec: [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by rburkartjo on 2010-07-28
tks ya'll will give it a shot and mark this as solved if it works

---

### Post by rburkartjo on 2010-08-07
tks for all your help. when i did this i put the recovered data on my / partition and maxed it out so i couldnt reboot. had to do a reinstall of the /. next time i will know better but the recovery program seem to work great. will put all recovered data on cd.

---

### Post by JustinR on 2010-08-07
> **rburkartjo said:**
> tks for all your help. when i did this i put the recovered data on my / partition and maxed it out so i couldnt reboot. had to do a reinstall of the /. next time i will know better but the recovery program seem to work great. will put all recovered data on cd.
 
Just for the record - if the seizure log was on the root(/) partition, then your writing data back to the hard drive again - which would have overwritten the log file! So next time, you could attach a flash drive/external hard drive and write the un-deleted file data there instead.

I recommend PhotoRec too - its great.

---

### Post by rburkartjo on 2010-08-08
tks jus for the info

---

