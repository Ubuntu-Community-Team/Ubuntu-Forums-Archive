---
title: "HDD format recovery ???"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by wasteman on 2010-08-11
I didn't wanted to format my hdd , it happened when i installed ubuntu 10.04 on my pc , now I'm wondering is there way to recover part of the data ... before format it was ntfs ... now its ext4 so pls tell me how to recover the data if it is possible , thx

---

### Post by pastalavista on 2010-08-11
> **wasteman said:**
> I didn't wanted to format my hdd , it happened when i installed ubuntu 10.04 on my pc , now I'm wondering is there way to recover part of the data ... before format it was ntfs ... now its ext4 so pls tell me how to recover the data if it is possible , thx

If you reformatted the whole drive when you installed, your data is gone. If you only formatted part of it (by first shrinking the Windows partition to make room for the Ubuntu partition which has to be ext4 or ext3) your data may be safe.

---

### Post by wasteman on 2010-08-11
I had ubuntu 9 and I've updated it to 10.04 ... and I had problems with my ATI Radeon hd 2600 pro video card ... the problem is still active and if I install the drivers from the official site , my monitor isn't working , the system is running ( i hear the login sound but have no pic) whatever , when I've installing the ubuntu 10.04 again ( after writing in forums , they've told me to install it again ) there were 2x 10.04 version of the ubuntu :-k and after that ... empty hdd , problems with video card , 6 mil wasted neurons

---

### Post by pastalavista on 2010-08-11
OK, sorry. Try installing one more time and this time when the installer gets to the partitioner, select "manually select partitions". Uncheck the format box for the first installation but format the second installation only as ext3 and give it a mountpoint '/home'

---

### Post by Mark Phelps on 2010-08-11
The more you mess with the drive, the worse the chance of being able to recovery ANYTHING.

If the data you want to recover was in an NTFS partition, then go to the Runtime Software website and download the trial version of GetDataBack for NTFS.  You will need to install this in another MS Windows machine -- because you can't recover data from a drive that is being used.  So, you would need to hook up the drive to another PC and do the recovery there.

The trial version won't actually recover the files, but it will show you how much data it WOULD be able to recovery.

Be patient!! Data recovery can take HOURS.  Best to run it overnight and see what it has found in the morning.

IF it finds most or all of your files, you will have to purchase it to do the actual recovery.

And, yeah, there are FREE tools available -- but as I said, the more you mess around with this drive, the greater the chance you won't be able to recovery anything.

---

### Post by wasteman on 2010-08-11
> **Mark Phelps said:**
> The more you mess with the drive, the worse the chance of being able to recovery ANYTHING.

If the data you want to recover was in an NTFS partition, then go to the Runtime Software website and download the trial version of GetDataBack for NTFS.  You will need to install this in another MS Windows machine -- because you can't recover data from a drive that is being used.  So, you would need to hook up the drive to another PC and do the recovery there.

The trial version won't actually recover the files, but it will show you how much data it WOULD be able to recovery.

Be patient!! Data recovery can take HOURS.  Best to run it overnight and see what it has found in the morning.

IF it finds most or all of your files, you will have to purchase it to do the actual recovery.

And, yeah, there are FREE tools available -- but as I said, the more you mess around with this drive, the greater the chance you won't be able to recovery anything.

thank you very much for the info , I've other pc which has windows on it ... I hope to find free solution for restoring the files (other programs which someone had already used or keygen for the GetDataBack) ... other suggestions :rolleyes:

---

### Post by varunendra on 2010-08-11
> **Mark Phelps said:**
> If the data you want to recover was in an NTFS partition, then go to the Runtime Software website and download the trial version of GetDataBack for NTFS.  You will need to install this in another MS Windows machine -- because you can't recover data from a drive that is being used.  So, you would need to hook up the drive to another PC and do the recovery there.

Well.... [Hiren's Boot CD]("http://www.9down.com/Hiren-s-BootCD-10-6-352820/") contains a 'Live XP' session from where you can run fully functional inbuilt copy of Get Data Back (and many other commercial software)! However, I'm doubtful about its legality since it contains many fully functional powerful commercial tools and yet is distributed free!

Anyways, I also recommend GetDataBack for such scenarios since it has saved me many times before from data-loss, sometimes when other tools failed. However, I've also witnessed a couple of occasions when it failed & it was surprisingly 'TestDisk' that saved me. Once it was RTools (commercial again- for windows / linux / OS independent Live CD) which I still assume to be most efficient data recovery tool!

> **wasteman said:**
> thank you very much for the info , I've other pc which has windows on it ... I hope to find free solution for restoring the files ... other suggestions :rolleyes:
With Hiren's Boot CD, you can boot into Live 'Mini Windows XP' session directly from CD without installation. After loading, it will automatically present you a huge list of both free & commercial tools where you can find GetDataBack for NTFS also.

---

