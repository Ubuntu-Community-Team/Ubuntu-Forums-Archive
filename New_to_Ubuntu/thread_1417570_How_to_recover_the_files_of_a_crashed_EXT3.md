---
title: "How to recover the files of a crashed EXT3?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by patrick295767 on 2010-02-27
Hello,

I tried testdisk, and it helped a bit. So now the only way is photorec to check cluster per cluster teh data.
OK, but when you have not another harddisk to backup the disk, how do you do? Photorec does not that

So is there a guy that coded a good data recovery for linux? 
Come on, there is only photorec :! we are in 2010 now and still so less linux programs

---

### Post by skymera on 2010-02-27
How did the files corrupt?

Did you disable journaling or power off during an FSCK?

---

### Post by click4851 on 2010-02-27
you might try something with rsync?

---

### Post by patrick295767 on 2010-02-28
> **skymera said:**
> How did the files corrupt?

Did you disable journaling or power off during an FSCK?

No I actually use dd 
```
dd if=myimageof16mboffat16.img of=/dev/sda_my2gbext3
```
Yeah, I killed my disk, I was tired, or I dont know the crap what I did that day.

 
After several times using Photorec, it is basic program that has no other better alternative. It can try to recover files. But one is limited by:
- one cannot select a new type of files, example avi extensino isnt in there even ;) and one has a limited possibilities of files
- it is not recovering folders, because it doesnt care.
- it cannot create a new *.img (raw or gz) file of a crashed harddisk, *.img that is readable my mounting + loop
- one have to have a larger size harddisk to recover your data
- one has to seek the whole harddisk, and the user cannot have a list of files, and then give the possibility to recover (copy) only the one wanted to be recovered
- photorec does not recover the filenames even,

what a mess after a photorec recovery, better not to use it ;)

Or is there better program / code from Freebsd or MacOsX or windows (all platform) that we could compile? I mean that cannot be. In Windows there is so many apps and disk utilities.

So it is better to use the NTFS rather than EXT3. 
I am not willing to buy a new harddisk because there is no tools to recover harddisk under linux. 

foremost works only with an image.dd, also that is in raw and not gz or tar.gz tinier. 

photorec does not recover folders and filenames + you need a similar size harddisk to recover your files. How do you do if you are poor or are a student? wasnt Linux made for students at the beginning or for studying Unix, too expensive at that time ?

So solution : use Windows, you pay but you do not loose you data.

---

### Post by patrick295767 on 2010-10-17
> **patrick295767 said:**
> No I actually use dd 
```
dd if=myimageof16mboffat16.img of=/dev/sda_my2gbext3
```
Yeah, I killed my disk, I was tired, or I dont know the crap what I did that day.

 
After several times using Photorec, it is basic program that has no other better alternative. It can try to recover files. But one is limited by:
- one cannot select a new type of files, example avi extensino isnt in there even ;) and one has a limited possibilities of files
- it is not recovering folders, because it doesnt care.
- it cannot create a new *.img (raw or gz) file of a crashed harddisk, *.img that is readable my mounting + loop
- one have to have a larger size harddisk to recover your data
- one has to seek the whole harddisk, and the user cannot have a list of files, and then give the possibility to recover (copy) only the one wanted to be recovered
- photorec does not recover the filenames even,

what a mess after a photorec recovery, better not to use it ;)

Or is there better program / code from Freebsd or MacOsX or windows (all platform) that we could compile? I mean that cannot be. In Windows there is so many apps and disk utilities.

So it is better to use the NTFS rather than EXT3. 
I am not willing to buy a new harddisk because there is no tools to recover harddisk under linux. 

foremost works only with an image.dd, also that is in raw and not gz or tar.gz tinier. 

photorec does not recover folders and filenames + you need a similar size harddisk to recover your files. How do you do if you are poor or are a student? wasnt Linux made for students at the beginning or for studying Unix, too expensive at that time ?

So solution : use Windows, you pay but you do not loose you data.

I use now JFS and to time to time :
touch /forcefsck

and never got a single crash anymore !! JFS rocks over ext3

---

### Post by Mustache Villain on 2010-10-17
Follow this [Data Recovery guide]("https://help.ubuntu.com/community/DataRecovery") from the Ubuntu wiki.

---

