---
title: "Can I start PhotoRec from a specific sector of my choice?"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by taminrob on 2009-03-14
Need some information from some of you more knowledgeable Ubuntu users.  I recently killed my hard drive during repartitioning and am in the process of running PhotoRec to recover my data.  This process is going well but very slowly...so far it has been running for 3 1/2 weeks and is still not even half complete (120gb drive).  At this point, I am ready to install a new HDD and do a fresh install of Ubuntu but I am leery about stoping PhotoRec without knowing if, when I start it again, I can begin it at a point of my choosing, such as the sector it left off on. Is this possible?

I know that I have bad sectors on my drive, but is is normal for it to take this long? Is there a better way that I can do this?  Any ideas or suggestions will be greatly appreciated.

---

### Post by zabien1970 on 2009-03-14
At their website in directions it says if you stop it will ask to resume next time you run photorec. Look at the bottom of this link

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It also mentions for large hard drives to run testdisk first which will be faster.
I've used photorec on 4 to 8 gig memory cards and it went fairly quick

---

### Post by taminrob on 2009-03-14
Thanks for that, but I guess my question is, when I swap out my old drive for my new one, I will be running PhotoRec on a different computer...one that I can let it run to its completion on without it interfering with day to day usage...will it still ask to resume?  I am running it from a live cd and will have the drive in an enclosure with an esata cable connection.

---

### Post by budsandbytes on 2009-07-23
Sorry, this is probably a dead thread by now- but I came looking for the same answer and was disappointed- so now that I've figured it out, here's the answer:

In the directory you start photorec from (or your home directory) it will place a photorec.ses

If you want to manually manipulate this file, you can change the sector range checked.

Mine looks something like:

#1237368742
/dev/sdf partition_i386,1,blocksize,4068,fileopt,..............
[firstsector]-[lastsector]
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@...

I had a weird drive that I was connecting via USB that would end up with a different designation in /dev/ every time I plugged it in- it wouldn't mount, but photorec would pull stuff from it.  I had to skip over 100 sectors or so every time photorec locked up to get it going again.

3 days later, voila, files!

---

### Post by tanoloco on 2011-07-16
Hello,

sorry to reply to such an old thread, but I'm in the same bad situation.

If you can read this, and if you remember how, do you mind to explain better how to modify photorec.ses in order to go on?

I've got this output```
#1310772507
/dev/sdb partition_i386,5,blocksize,1024,fileopt,1cd,enable,7z,[...],enable,zip,enable,options,paranoid,keep_corrupted_file_no,mode_ext2,wholespace,search,inter
18432-18433
[...]
42611198-42611223
42611232-42611383
42611384-42612023
[...]
45711358-467425279

```

photorec always hangs at sector number 42611280
this is between the range 42611232-42611383 written in the ses file.

I tried to comment it with #
-> result photorec crashes

I tried to delete it
-> result photorec starts from 0 and hangs at same point

I tried to cancel any range before this, included this one
-> result photorec starts from the hanging point and remains hanging

I tried cancel also the next range in list
-> same result as above

How have you figured it out?

Hope in an answer ...

---

### Post by tanoloco on 2011-07-17
At the end I gave up.
I haven't figured out how to start photorec from a specific sector
but I discovered that changing the options directly from tyhe interface in order to select only the filetype I want it doesn't hang and goes to the end recovering everything I aspected.

Hope this may help
Cheers

---

### Post by sicklittlemonky on 2011-10-22
For future reference, PhotoRec 6.13(WIP - Work In Progress, currently) correctly resumes from a previously stopped scan at the appropriate sector. And you can hack the start sector.

The sector to restart at is near the beginning of the .ses file, so this is handy for hacking around bad sectors. It's also handy when a file scan goes bad and never ends. I've seen it trying to find the end of a .doc file at 1GB+ ... luckily now you can (S)top the scan, quit out and bump the start sector. I'll request a feature for this.

Cheers,
Nick.

---

### Post by itismike on 2011-11-02
thanks Nick. I'm working on one now that had a segfault half way through a 500 GB drive. My .ses file is just 40 K of:```
@^@^@^
```
I may install the beta PhotoRec manually but am still a little confused at the difference between it and TestDisk. Both seem to recover accidentally deleted files. Is it that PhotoRec is better for images?

---

### Post by itismike on 2011-11-03
Hi Nick. I grabbed version 6.13 and it was able to complete the whole drive without segfaulting! Much thanks!!!

Larry, running from a live CD you won't be able to save or edit the session file.

-Mike

---

### Post by www.rzr.online.fr on 2011-11-12
hi

How are you using the resume recovery mode ?

I have 500GB (XFS) to recover , and I dont know how to script that tool, I wish It could save restart point periodically ...

Regards

-- 
[http://rzr.online.fr/q/recover](http://rzr.online.fr/q/recover)

---

### Post by itismike on 2011-11-12
I don't understand the question. Have you gotten the version Nick mentioned (6.13)? Did you run it, and if so what result did you get? 

By 'I don't know how to script that tool', do you mean you don't understand how to run it? If so, basically you need to identify your disk:```
sudo blkid
```then run photorec on the disk you want to scan:```
sudo photodisk /dev/sdc
```

Once you get the above working, if photorec needs to be restarted it should pick up where it left off. If it does not, it sounds like version 6.13 allows you to edit the photorec.ses file to have it start where you tell it.

---

### Post by dukemaster on 2012-01-25
Hi, you can resume editing the photorec.ses , but you first need to photorec make a first resume session .


So, let them pass over 1 minute of recover and stop it. then quit photorec. Enter again and put "Y" to  resume the last session, if it work ? now you can stop it again and quit. Edit the photorec.ses and put the sector that you want , an example:

```


#1310772507
/dev/sdb partition_i386,5,blocksize,1024,fileopt,1cd,enable,7z,[...],enable,zip,enable,options,paranoid,keep_corrupted_file_no,mode_ext2,wholespace,search,inter
18432-4611198
4611198-4611223
**600000000**-3900653678

```

and then open again and click Y, un about 20 seconds the number change to your sector :D it work for me , in mac . and a 2TB Drive :P

Bye and good luck

---

### Post by andrew.taylor on 2012-01-27
hi all. is there a way to tell photorec to start searching in a specified directory instead of searching the whole partition? or a way to search only for the most recent files, avoiding files deleted two years ago?

thanx.

---

