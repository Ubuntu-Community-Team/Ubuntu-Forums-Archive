---
title: "Attempt #2 with Ubuntu"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by CBR_Rob on 2010-03-30
Ok I am going to give up on having Ubuntu on my Toshiba. That laptop may just get recycled down to my wife. I am going to try the dual boot on my Dell Inspiron E1505. My question since I will still be running Windows XP with it on a dual boot and want to create a partition just for data storage how should I split up my 250 gig hd and will Ubuntu be ok with my data being stored on another partition and will it be ok sharing with Windows?

---

### Post by hardbeans on 2010-03-30
From my experience, it's best to have your main operating system on the largest partition. But it depends on how much storage space you want. Ubuntu will run fine on a small partition with a larger one for storage beside it. As far as easily accessing your other partitions, I'm running ubuntu, mac, and windows and I can access the mac and windows partitions from ubuntu just fine with no problems.

---

### Post by J V on 2010-03-30
It takes NTFS fine... I have a little guide on sharing your ~ with windows:
> **Sharing your home folder with windows**
Linux shortcuts (known as symlinks) act just like folders, so if a shortcut called shorty leads to randomfolder which contains test.txt, you can also access it with shorty/test.txt

Now, while windows has difficulty (At best) with accessing the Linux file system, you can still share your documents.

By replacing standard folders like Pictures with symlinks to /media/windowsdrive/Users/<yourname>/My Pictures etc, all files saved to pictures, will actually be saved to the windows drive, meaning you can access and modify your stuff from both windows and Linux.

Settings for some programs can also be linked, Firefox settings are similar on both OSs for example, so you could link your .mozilla folder to the similar location on your windows drive.

Suggest Primary NTFS for windows, mabey 60 gigs?
Rest in extended...
1G swap
10G root
40G home
rest in data partition

---

### Post by jflaker on 2010-03-30
Back up your data FIRST, then go for it.

Ubuntu will live comfortably on 6GB.  Here is where you should probably create a few GB partition just for your data so it is accessible to both systems...You can mount the windows partition from Ubuntu, but Windows will not mount the Ubuntu partition....

---

### Post by 2hot6ft2 on 2010-03-30
If it were me and since you want opinions I would split it up like this.
XP 35-40 GB (depending on how much stuff you typically keep in xp)
Ubuntu 35-40 GB  (depending on how much stuff you typically keep in ubuntu)
Linux swap 2 GB
os2os shared NTFS partition would get whatever is left.

If I was going to use a separate / and /home then
/ 10 GB
/home 30 GB

Pic attached of mine right now, sda2 is 9.10 the rest have labels. It's a 500 GB Drive. Win 7, sda8 is encrypted it's not a problem with it.

---

