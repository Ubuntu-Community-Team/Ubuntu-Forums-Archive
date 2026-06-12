---
title: "Ntfs?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Oloty on 2010-10-22
Well when I put the Ubuntu CD in I accidentally had it install over Windows 7. Now I'm trying to reinstall Win 7 but it says that my drive needs to be NTFS. How can I make it NTFS?

---

### Post by sandyd on 2010-10-22
> **Oloty said:**
> Well when I put the Ubuntu CD in I accidentally had it install over Windows 7. Now I'm trying to reinstall Win 7 but it says that my drive needs to be NTFS. How can I make it NTFS?

Boot up from the livecd.

post output of
```

sudo fdisk -l
```

and next time, -> [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

---

### Post by JustinR on 2010-10-22
> **Oloty said:**
> Well when I put the Ubuntu CD in I accidentally had it install over Windows 7. Now I'm trying to reinstall Win 7 but it says that my drive needs to be NTFS. How can I make it NTFS?

Put the Ubuntu CD back in your computer and boot up - click 'Try Ubuntu before Installing'. 

Once that boots up go to System > Administration > Disk Utility.

Find your Hard Drive, click 'Format Drive' and press the 'Format' button. Then click the huge empty partition and click the button 'Create Partition' and select NTFS. Then restart the computer with the Windows Disk.

---

### Post by yetiman64 on 2010-10-22
> **Oloty said:**
> Well when I put the Ubuntu CD in I accidentally had it install over Windows 7. Now I'm trying to reinstall Win 7 but it says that my drive needs to be NTFS. How can I make it NTFS?

On the Ubuntu live cd is a program "gparted", available from System > Administration > Gparted. With it you can repartition or just format an existing partition to NTFS for installing Win7 to.

Edit: JustinR's suggestion is probably a better one for a person not experienced at partitioning (if that is your situation)

---

### Post by Wild_Wes on 2010-10-22
You could get ultimate boot cd, burn it to a cd, then boot to it. Hit "start", "programs", "Partition", "EASUS Partition Manger". When the program starts, delete all partitions. When it asks you if you want to delete partition and destroy data or just delete partition, choose delete partition. When that finishes, shut down the computer. Then go back to installing OS. Install windows first. If this doesn't work, let me know.

---

