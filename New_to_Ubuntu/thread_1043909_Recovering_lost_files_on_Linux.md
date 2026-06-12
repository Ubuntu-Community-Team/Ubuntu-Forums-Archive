---
title: "Recovering lost files on Linux"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-01-19
Well, this has got to top all the stupid things I`ve ever done (on a computer anyway). It would have been ten times cheaper for me to just get paid hosting, but no I had to try and learn about servers :)  I had wrongly thought that somehow, my home directory had gotten ftp`d `out there` (though I couldn`t remember doing it so...) because I saw it (with all the sub-directories of pictures, documents etc.) in the right hand `panes` or panels or whatever, that normally means what has been ftp`d,  but it was just my local server,(so the same local files that appeared on the left side) because I couldn`t manage to get the online one running.  Late at night and lack of sleep and...I deleted all those files,  so I lost almost 2 years worth of family pictures of my 7 year old and 15 year old and my dad...again! I had to pay big bucks to recover before from a hard drive crash (windows viruses).  Also my backed up pic disks have disappeared.  I am just wondering if it is harder to recover files from a Linux system, or if there is anything special that has to be done.  I may never speak to myself again grrrrr.

---

### Post by iaculallad on 2009-01-19
Try using [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by emarkd on 2009-01-19
Your odds of success go way up if you stop using that harddrive ASAP.  If you're still working from that computer you may be overwriting the data at any time.  You should turn off that computer and use another one to attempt the recovery.

Good luck.

---

### Post by eatberrys on 2009-01-19
Well how bad do u want the files ? cuse if u want them really bad boot to a live cd
make a bit for bit copy of the hd to external media useing the DD command then install foremost and use it to recover the files.

---

### Post by doas777 on 2009-01-19
Best Practice Steps for recovering deleted data:

1) Shut down the system immediately. it is even recommended in some circles, that you pull the plug, rather than shutdown gracefully. of course this may cause other problems including dataloss.

2) boot off a live CD like the [ubuntuRescueRemix]("http://ubuntu-rescue-remix.org/")

3) use a tool like partImage to create an image file of the drive that contained the deleted data, saving it to another storage device. 

4) mount the image and use a recovery tool like photorec as the kind person above suggested, to recover the required files.

if you follow these steps, you have the best likelyhood of recovering your data, but even then it can be a crap shoot. 

weird things happen to storage locations when the operating system has decided to forget about them. I recovered some word documents on a wintel box a few weeks ago. they we're all liberally scribbled on, with the contents of the PCs clipboard at time of shutdown.

good luck,
franklin

---

### Post by Nnako2 on 2009-02-22
Hi, as i couldn't an iage file, I tried to run photorec but at the first step, when I have to select the disk that holds the lost files, i can only see my 500 gb external hdd :S


Thanks again

---

### Post by bodhi.zazen on 2009-02-22
See :

General : [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) (needs work)

    How to : [http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by mal_conductor on 2009-03-29
these are my notes on how to recover files using testdisk and photorec.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

