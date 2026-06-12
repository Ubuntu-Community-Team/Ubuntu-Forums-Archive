---
title: "recommended recovery CD?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by garyed on 2010-02-19
I need a bootable cd that can recover deleted files from a Windows partition. The Ubuntu live CD will boot OK but it can't find the files since they've been deleted by a Windows recovery mess up. I don't know if its possible but I want to give it my best shot to get back years of data that was erased & not backed up.
Thanks for any help,

---

### Post by audiomick on 2010-02-19
Hallo.
Not having had any experience, I can't make a direct recommendation other than to look here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bumanie on 2010-02-19
Sorry to hear about the data loss. 
You should clone the windows partition to another partition or preferably an external hard drive, that way you can try the retrieval from the clone, thus leaving the original windows installation in its present condition. Thus if you muck up the data retrieval, you can re-clone the original windows installation again. I would clone using dd commands, but there are numerous gui-based tools available, none of which I have used. There are even a couple of forensic 'quality' cloning tools such as guymager and air, that are both gui-based.
99% of the time, as long as the information has not been over-written, the files are usually retrievable. In the first instance you should look at tools such as [ntfsundelete]("http://manpages.ubuntu.com/manpages/jaunty/man8/ntfsundelete.8.html") and [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")
There is also photorec (on the testdisk site) that reads raw data off the disk and is filesystem independent. There is also scalpel and foremost, that do much the same thing. Magicrescue is another tool - not sure if supports ntfs or not.
It is advised not to rush in to these things, if you have not done them before. Read all documentation available and look for "How to's" on the internet. The information is important to you, so take time reading and making sure you understand what to do before attempting things. You first step should be to clone the windows partition/drive.Then you can try the data retrieval techniques and as stated, if things muck up, you can always clone the windows partition/drive a second time.
Hope this helps a bit.

---

### Post by garyed on 2010-02-19
Thanks for the replies,
Sorry for not following up but I had to go to work right after I posted this question.
thanks again

---

