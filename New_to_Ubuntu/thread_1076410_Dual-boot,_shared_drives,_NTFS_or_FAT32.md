---
title: "Dual-boot, shared drives, NTFS or FAT32?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-21
Hi all - dual boot U8.10 & Vistax64.

When I partitioned my single laptop HDD I set up 250 GB of FAT32 to share with both OS, that after seeing all kinds of web talk about linux only see FAT etc etc..

Installed U8.10 and it not only sees my Vista OS but lets me  mount. I don't know how good an idea that is..but thats another question?

Opinions please - should I rejig my shared Extended and Logical partitions to NTFS and happily share, or keep as FAT32 and leave well enough alone?

Cheers

dmc

---

### Post by 4Orbs on 2009-02-21
Maintaining an NTFS shared partition is easier, mainly because the Vista tools can defragment ntfs in a fraction of the time compared to defragmenting fat32.

---

### Post by Crandom on 2009-02-21
I would convert them to ntfs - it has many more advantages than FAT32 [{link}](http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx) and is now well supported in linux with ntfs-3g.

You don't need to reformat the FAT32 drives, you can just use the [FONT="Lucida Console"]convert[/FONT] command in vista. To do so just type this command into a Command Prompt in vista (Start > Run > "cmd"):
```
convert [drive_letter]: /fs:ntfs
```
If you need to dismount the drives first use this command:
```
convert [drive_letter]: /fs:ntfs /X
```
More info at [http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

---

### Post by Tatty on 2009-02-21
I agree with crandom. Ntfs support in linux is very mature now. Most sources which recommend fat are usually quite old now.

---

### Post by Mark Phelps on 2009-02-21
> **deadmanschest said:**
> 

Installed U8.10 and it not only sees my Vista OS but lets me  mount. I don't know how good an idea that is..but thats another question?

dmc

NOT a good idea to mount your Vista OS unless you mount it read-only.  Why? Because any irregular shutdown will set the Vista OS as unmountable under Linux -- which require you to boot into Vista and run a chkdsk on it.  But if it gets corrupted, you won't be able to boot into Vista to fix it. Results in a catch-22.  Better to mount it read-only.

---

### Post by deadmanschest on 2009-02-21
Hi everyone - thanks collectively for the shared wisdom, had to be away for a bit, so slow to respond..

I will convert the FAT32 extended partition to NTFS, and I will make the VistaOS drive and its accompanying Data partition 'read only' from U8.10, if I can figure out how to do that....hehe..

Thanks to all;

Cheers

dmc

---

### Post by jerome1232 on 2009-02-21
> **Crandom said:**
> I would convert them to ntfs - it has many more advantages than FAT32 [{link}](http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx) and is now well supported in linux with ntfs-3g.

You don't need to reformat the FAT32 drives, you can just use the [FONT="Lucida Console"]convert[/FONT] command in vista. To do so just type this command into a Command Prompt in vista (Start > Run > "cmd"):
```
convert [drive_letter]: /fs:ntfs
```
If you need to dismount the drives first use this command:
```
convert [drive_letter]: /fs:ntfs /X
```
More info at [http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

Nice tip, didn't realize xp and vista had a conversion tool built in. My father-in law just got a tv tuner card and was asking me why he couldn't save videos over x amount of hours, turns out he was saving them on a fat32 partition, now I can convert it ntfs without shuffling files around.

---

