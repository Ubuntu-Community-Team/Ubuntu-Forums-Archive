---
title: "LOst PIctures While Installing, can I recover"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by avacomputers on 2009-07-20
I was on XP and installed UBuntu on my entire disc and forgot to back up one folder with some pics. Is there anyway to recover this.

Andrew

---

### Post by ugm6hr on 2009-07-20
If you were on XP while installing Ubuntu, you must have used Wubi, which will not wipe XP.

If you installed using the whole HD from the LiveCD, then your files have all been erased.  Recovering them will be almost impossible unless you pay a data recovery specialist to do it.

For future reference, never install an OS without a bcakup of your files, even if intending to dual-boot.

---

### Post by cariboo on 2009-07-20
I would suggest you install the testdisk package, it is in the repositories. Go to System-->Administration-->Synaptic Package Manager and search for testdisk. One of the programs included in the package is called photorec. It is a command line tool. Have a look [here]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive") for a howto.

---

### Post by rbc on 2009-07-20
Stop booting to the hard drive until after you have used photorec to attempt the recovery. Boot using the LiveCD. You will still be able to download testdisk/photorec to RAM. You will also want some other media, other than the hard drive in question, to save the save the recovered files to

---

### Post by avacomputers on 2009-07-20
I  booted from the cb and install UBuntu over the entire drive.

---

### Post by Yvan300 on 2009-07-20
Well if they are that important, then the easiest, but not most cost effective way would be to contact a data recovery specialist. And even then, they may not be able to retrieve your info. Btw the more you use your pc, the less likely your data will be recoverable.

---

### Post by avacomputers on 2009-07-20
I am running photorec and so far recovered 3000. DON't know if the ones I am looking for are there but fingers crossed.

---

### Post by rbc on 2009-07-20
Good to hear. I have always had pretty good luck with photorec, and it, alone, does not do any further damage, just in case you end up having go for professional help

---

### Post by avacomputers on 2009-07-21
Sweet. I was able to recover all the pictures that I needed and learnt a valuable lesson. "BACK UP". Now the folders that were created with the recovery all have a lock and I can't delete them. Any help would be awesome.

---

### Post by rbc on 2009-07-21
So, your computer is back up and running from the OS install on the hard drive, not the Live CD, right? If so, where are the pictures you want to delete? On the internal hard drive, external hard drive? Basically, what's the path/to/the/directory where the photos are stored?

---

### Post by nothingspecial on 2009-07-21
> **avacomputers said:**
> Sweet. I was able to recover all the pictures that I needed and learnt a valuable lesson. "BACK UP". Now the folders that were created with the recovery all have a lock and I can't delete them. Any help would be awesome.

Open a terminal (in your menu accessories > terminal)

Type ```
gksudo nautilus
```

The file manager will open and you will be able to delete that folder. Close it imediately and make sure you only delete the folder you want to. After all you`ve already lost your pictures once.

---

### Post by avacomputers on 2009-07-21
> **rbc said:**
> So, your computer is back up and running from the OS install on the hard drive, not the Live CD, right? If so, where are the pictures you want to delete? On the internal hard drive, external hard drive? Basically, what's the path/to/the/directory where the photos are stored?

I am on the OS running from HD. And the recover pictures are now safely on an External Drive. 

> **nothingspecial said:**
> Open a terminal (in your menu accessories > terminal)

Type ```
gksudo nautilus
```

The file manager will open and you will be able to delete that folder. Close it imediately and make sure you only delete the folder you want to. After all you`ve already lost your pictures once.

THanks I will report back.

---

### Post by avacomputers on 2009-07-21
> **nothingspecial said:**
> Open a terminal (in your menu accessories > terminal)

Type ```
gksudo nautilus
```

The file manager will open and you will be able to delete that folder. Close it imediately and make sure you only delete the folder you want to. After all you`ve already lost your pictures once.

Worked like a charm. Thanks.

---

