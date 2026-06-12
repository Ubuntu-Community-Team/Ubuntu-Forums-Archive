---
title: "external hdd mess up"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by martin saint martin on 2009-05-15
a friend and i installed 9.04 on his computer the other night.  during the installation we noticed that ubuntu was installing itself on his external hdd not his internal hdd, so we literally pulled the usb plug and restarted the installation.  the install went fine, but now the data on the external hdd can not be "seen" by ubuntu.  we choose a guided install into a new ext3 partition not the "use entire drive option."  my question is:  is the data lost or is there a way to retrieve it?

---

### Post by Kosimo on 2009-05-15
During the first installation did you choose: "Use the entire drive?"

If yes.... You don't have too many chances to recover the data... :(

---

### Post by reg4c on 2009-05-15
If you chose "Use entire drive" there is very little chance of recovering data since Ubuntu will first format the drive. 

Try using Windows to read the drive and see whether it can recognize anything and perhaps recover.

---

### Post by martin saint martin on 2009-05-15
i did not choose "use entire disk."  i choose "use free space"

---

### Post by zeroseven0183 on 2009-05-15
> **reg4c said:**
> Try using Windows to read the drive and see whether it can recognize anything and perhaps recover.

If Windows recognizes the drive, try using [Final Data]("http://www.finaldata.com") for recovering your files.

My goodness... I'm helping troubleshoot a Windows problem on a Linux forum.

---

### Post by alwayshere on 2009-05-15
try using photorec its a good recovery app that will do the job google linux photorec also i think its in synaptic .
note its a terinal type app with no fancy grapics just bios type thing easy and good to use.

---

### Post by martin saint martin on 2009-05-16
windows xp will tell us that the drive is corrupted.  in ubuntu the drive can be mounted and the amount of free/used space is defined, but when the drive is opened, using natalius, there are no files/folders listed in the window.  could the data on the external be cloned/copied to the internal, then, at that point, could the data be "seen"/accessed?

---

### Post by NHArticleTen on 2009-05-16
> **martin saint martin said:**
> windows xp will tell us that the drive is corrupted.  in ubuntu the drive can be mounted and the amount of free/used space is defined, but when the drive is opened, using natalius, there are no files/folders listed in the window.  could the data on the external be cloned/copied to the internal, then, at that point, could the data be "seen"/accessed?

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)


[http://www.diydatarecovery.nl/index.htm](http://www.diydatarecovery.nl/index.htm)

---

### Post by KCormier on 2009-05-16
I've made this mistake before.  I know the files are recoverable, at least most of them.

I overwrote 3 ext3 partitions with one large one AND installed ubuntu over them.  I lost a little bit of data at the beginning of the first partition, but recovered EVERYTHING later on the drive.

You should be able to get mostly everything back.

I used testdisk to recover all my data!  photorec works well as well!

-Kevin

---

### Post by NHArticleTen on 2009-05-16
> **KCormier said:**
> I've made this mistake before.  I know the files are recoverable, at least most of them.

I overwrote 3 ext3 partitions with one large one AND installed ubuntu over them.  I lost a little bit of data at the beginning of the first partition, but recovered EVERYTHING later on the drive.

You should be able to get mostly everything back.

I used testdisk to recover all my data!  photorec works well as well!

-Kevin

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

