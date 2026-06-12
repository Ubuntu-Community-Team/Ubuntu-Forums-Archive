---
title: "Jaunty. Input/Output issues on 1TB HDD. Cannot write  read"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by wetinwales on 2009-07-15
Jaunty on 64 bit machine. AMD. two HDD 160Gb system drive and 1TB HDD general storage. All as per the Heron 8.04 system I had on an older machine set up the same way. I'm trying to transfer everything over to the 'new' 1TB HDD.

Had problems with 'permissions'.
Posted too many times - sorry:-
[http://ubuntuforums.org/showthread.php?t=1211357](http://ubuntuforums.org/showthread.php?t=1211357)
[http://ubuntuforums.org/showthread.php?t=1211209](http://ubuntuforums.org/showthread.php?t=1211209)
[http://ubuntuforums.org/showthread.php?t=1205049](http://ubuntuforums.org/showthread.php?t=1205049)
(demonstrating my inability to understand concepts of permissions and mounting HDDs etc)
Have been through pretty much all of these above posts learning some things but have obviously messed up.

I now cannot write to my 1TB HDD (second drive sdb1)
The message most commonly is Input/Output errors.. new one to me.
I assume it is Input/Output errors to do with the 1TB HDD.

Cannot read many files from it either. Can read some.

Half the files thereon were transferred from a (fat32) Ext USB where they are stored. These (mostly jpegs) are readable.

Half were transferred by putting the old HDD into the new machine and copying over. These seem to be ones which are corrupt, missing or otherwise not accessible. However they were accessible to begin with.

The second 1TB HDD keeps dumping its directory and file listings. 
I re-boot to start again; get the listings back, but not the actual files.

Generally Jaunty is great and the system HDD (160Gb) and files I have on it are fine.

I am now deeper out of my depth. Can anyone help?

Daf

---

### Post by wetinwales on 2009-07-15
I believe that all along I may have a faulty HDD (1TB HDD)
The 'Input/Output error' appears now for everything. I can not delete read or write to sections of the drive; only see listings.

Most of the info on forums suggests HDD faults.

Anyone comment?
Anyone with similar ?

Thanks
Daf

---

### Post by Mark Phelps on 2009-07-16
I'm almost afraid to ask ... but is the "bad" drive A Seagate 1TB?  Those have had a really bad reputation for failures, even after Seagate pushed out supposed firmware upgrades.

If it is a Seagate, and you have an MS windows box you can connect the drive to, you can download and run SeaTools. It will scan the drive for errors and if it finds some, you may be able to get a drive exchange out of Seagate.

---

### Post by wetinwales on 2009-07-16
Hello
No its a Western Digi....SATA

The input output errors became epidemic. The drive would not last more than a few clicks or minutes before loosing its file listings - but keeping its directory listings.

I removed it from the tower - and set it up on my desk perched on a plastic box; reconnected all after blowing out the plugs/sockets.

It runs sweet as you like and Ive hammered it - opening closing and file checking.

There were perhaps microns of dirt on the gold  contacts. Or a mechanical situation inside (less likely).
Impedance becomes a bigger issue the higher the frequency and a fly fart on a contact can be catastophic. Also heat, as the drive warms up etc etc etc

Some of my desperate posts as above were created by this developing fault and not by software issues. I simply hadn't understood how to report them.

Fingers crossed its working swimmingly well. (and no corrupt files yet found) Course this all might herald some deeply intermittent and dangerous HDD fault.

Comments welcome from anyone !

Regards

---

