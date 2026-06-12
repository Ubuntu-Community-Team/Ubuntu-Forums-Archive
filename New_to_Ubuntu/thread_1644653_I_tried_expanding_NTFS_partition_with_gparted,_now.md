---
title: "I tried expanding NTFS partition with gparted, now it won't open"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by VivekT on 2010-12-13
I had some unallocated space on my hard drive, so I tried to expand one of my ntfs partitions using gparted. However right after it showed an error. When i booted Windows, The partition was showing as RAW and when i try to open it Windows asks me to format it. It had important data. Is it possible to recover this partition. I have no clue what to do. Thank you in advance.

---

### Post by oldfred on 2010-12-13
Because you resized it, you may not be able to recover the backup. But the NTFS partition is missing its boot sector. But beside recovery testdisk also has a rebuild capability.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by fly-by-night on 2010-12-13
Was the unallocated space directly next to the NTFS partition (on either side)?  

If not, you might have done "something else" by mistake.  The space can only be added to the partitions next to it, then passed left or right again to reach the intended target partition. 

If the process that wiped the disk was similar to formatting it you might be able to recover, but that's not my speciality (I do backups:D).

Also what Windows do you have.  I've seen somewhere that gparted have problems with Vista/7 and could also be with it's formatted NTFS partitions.  That however might've been fixed.

---

### Post by ajgreeny on 2010-12-13
The first thing to do, if you can mount and read that partition in Ubuntu, is make a backup of the files that are so important to you, either by simply copying them to your Ubuntu partition, in your home, or if needed onto an external USB drive.

I am aware that some people have had success shrinking ntfs partitions in Vista and Win7 with gparted, and you can certainly do it in WinXP.  However for future reference, it is much, much safer to use windows own disk management utility in Vista and Win7, even to shrink partitions, and it's definitely not a good idea to try to enlarge or move them using gparted as it seems to cause big problems.

I do hope you manage to get your windows back, or at the very least get your files from the partition, but I fear you may have a long road ahead.

---

### Post by VivekT on 2010-12-13
@oldfred   

I used the Advanced options in testdisk and fixed the boot sector thing but now windows shows it as a corrupt or unreadable partition. I guess I need to do the Deeper Search thing.

@fly-by-night

The unallocated space was next to the ntfs partition.
I have Windows Vista

@ajgreeny

I can't access it through ubuntu either


I saw that testdisk has this "image creation" tool. Should I make the image.dd file and try get my data from that?


Thanks for the response. I'll let you know how it goes. Thank you

---

### Post by oldfred on 2010-12-13
The one thing you cannot do in Linux is run Windows chkdsk. You can try that depending on how corrupt the partition is, it may repair it. you have to run chkdsk until it reports no errors.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Then if chkdsk fails you go back to testdisk.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by VivekT on 2010-12-13
chkdsk is not working. it is aborted each time. and testdisk says that mft is bad so it cannot repair it. 

When Deeper Search finishes, if I press P for any of the options, the program exits on linux live cd. and since it was taking so long i am thinking of dropping that idea.

Now i'm thinking of making an image out of that partition. i don't know how i'll access the .dd file though

Thanks for your replies

---

### Post by oldfred on 2010-12-13
Depending on the size of the drive deep search or the photorec recovery of files can take all night. It has to scan drive and look for file signatures.

---

### Post by VivekT on 2010-12-14
Thanks everyone. It is fixed now. I could figure out the Deeper Search thing and now everything is showing perfectly as it was.

---

