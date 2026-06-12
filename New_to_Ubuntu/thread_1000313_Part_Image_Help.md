---
title: "Part Image Help"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by fishman78 on 2008-12-02
Hi Everyone,

    I am trying to make an image of my entire drive for quick backups.  I am using partimage as recommended by many.  My problem is that partimage is trying to save the image to the swap partition (and ofcourse runs out of room)  How can I change the target drive to my USB HDD or at least another partion on my drive??  Any help would be greatly appreciated.  Thansk!!

fishman78

---

### Post by fishman78 on 2008-12-03
Could anyone tell me a different program I could use to make a hot backup of my ubuntu??  Thanks!

---

### Post by bumanie on 2008-12-03
As it's the entire drive you want to image use dd commands in terminal, it's the easiest thing in my opinion. > dd if=/dev/sdx of=/dev/sdxSubstitute your drive letter for the x eg if  your internal drive is sda and the external sdb the code would be dd if=/dev/sda of=/dev/sdb

---

### Post by Michael.Godawski on 2008-12-03
A lot of questions dealing with backups since yesterday...

Have a look here:

[LIST]
[*][https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[*][https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)
[/LIST]

---

### Post by fishman78 on 2008-12-03
> **bumanie said:**
> As it's the entire drive you want to image use dd commands in terminal, it's the easiest thing in my opinion. Substitute your drive letter for the x eg if  your internal drive is sda and the external sdb the code would be dd if=/dev/sda of=/dev/sdb


Thanks!  Just to confirm, this won't mess up my current install?  and do I need an empty External HDD or can I use one with data already on it?  Thanks again!

---

### Post by Keen101 on 2008-12-03
You could try clonezilla. I've heard good things about it, and should be able to save image to external HDD.

[http://www.youtube.com/watch?v=whi9rFhldv0&](http://www.youtube.com/watch?v=whi9rFhldv0&)

[http://www.youtube.com/watch?v=ZyUwP4VHC0U](http://www.youtube.com/watch?v=ZyUwP4VHC0U)

---

### Post by bumanie on 2008-12-03
It should not upset your present installation as it is imaging the drive not formatting it. If you have an empty external drive that is of equal or greater capacity, you shouldn't need to do any more, other than have an ext3 filesystem available on it. If you have an external drive with information already on it, it would be best to make a folder for the image to placed in, but that involves more commands. Just remembered another way would be to boot up gaparted from a live cd (either the gparted live cd or the ubuntu live cd)- gparted has the ability to copy entire partitions and drives also. If I remember correctly, I used it once, (just to try it out) and it worked fine and it is a copy, as in the drive from which the copy is made is left in it's original condition. Personally I still prefer dd, due to its simplicity, but it is up to you. Sometimes with these things, doing some reading about various methods is a good idea, so that you can get a better understanding of how things work. By the way (this is important) you need to do the dd commands from a live cd because if the drive being copied is 'active' some of the data will be in use and thus may transfer in an unstable state. Good luck.

---

### Post by scorp123 on 2008-12-03
> **fishman78 said:**
> and do I need an empty External HDD or can I use one with data already on it? The command as written up there will overwrite whatever is on the target disk with whatever is on the source disk ... Technically "dd" doesn't care at all if the disk is empty or not, it does not make a difference. Either way the disk gets overwritten.

Please double-check and read the manual:  ```
man dd
``` ... feeding "dd" with the wrong parameters can do a lot of damage.

I personally am not such a big fan of "dd" as backup solution as it copies way too much, even empty sectors. If you copy a 250 GB disk partition that is only filled with 2 GB of data the resulting backup will still be 250 GB in size. Sure, you can use compression ... but it's way too inefficient in my opinion. I personally prefer copying just the files, either using "rsync" or putting them into "tar" archives.

---

### Post by bumanie on 2008-12-03
> **scorp123 said:**
> The command as written up there will overwrite whatever is on the target disk with whatever is on the source disk ... Technically "dd" doesn't care at all if the disk is empty or not, it does not make a difference. Either way the disk gets overwritten.

Please double-check and read the manual:  ```
man dd
``` ... feeding "dd" with the wrong parameters can do a lot of damage.

I personally am not such a big fan of "dd" as backup solution as it copies way too much, even empty sectors. If you copy a 250 GB disk partition that is only filled with 2 GB of data the resulting backup will still be 250 GB in size. Sure, you can use compression ... but it's way too inefficient in my opinion. I personally prefer copying just the files, either using "rsync" or putting them into "tar" archives.

Your input is valuable. I agree with what you say. It was not until a follow up post that fishman78 mentioned the possibility of a drive with information already there. That's why I have said he should read some things and also said that if being put on a drive with other information one would have to make a directory for it to be placed into. We all have our favouite ways of doing things. Your preferred methods are just as valid as mine :D But the original question was > I am trying to make an image of my **entire drive** for quick backupsYou are quite right that dd will copy everything including empty space.

---

### Post by scorp123 on 2008-12-03
> **bumanie said:**
> But the original question was: 
[INDENT]"I am trying to make an image of my entire drive for quick backups"[/INDENT]  Well ... IMHO the real question is how and where is the image supposed to be stored? If we really mean a disk image then the correct command would be: ```
sudo dd if=/dev/sdX of=/path/to/where/we/store/the/backup_disk.img
``` ... and that command should be best executed from a Live CD (as someone already mentioned). Doing that from a running system is not a smart idea ...  In any case that disk image could be compressed if space is an issue, even on the fly if you pipe it through a compressor, e.g. something like ```
dd if=/dev/sdX | gzip -9 > name.of.disk.image.gz
```

To uncompress you'd use something like 
```
cat name.of.disk.image.gz | gunzip | dd of=/dev/sdX
``` ... maybe thsose commands could even be more optimised?

However ... if on the other hand we're talking about disk cloning then you'd use something like this: ```
dd if=/dev/sdX of=/dev/sdY
```

The example that was given above was about disk cloning ... not disk imaging. Same command. Two different things :D

> **bumanie said:**
>  You are quite right that dd will copy everything including empty space. IMHO that would only make sense if you e.g. use encrypted partitions and you want to copy the whole thing without opening up the encrypted volumes and their contents. If you use that on a normal disk ... as I said, IMHO it's not very efficient. Taking and restoring backups even of only slightly used disks will take hours and when compression is used your CPU will have quite a load to work on. But yes ... as you said: what's right for me doesn't have to be right for you. I am just voicing my opinion here. Do whatever works for you and use whatever method is able to get your data back in one piece. Ultimately that's all that counts: getting the data back. If you can do it with "dd" then by all means do so. :)

---

### Post by fishman78 on 2008-12-03
Hey Guys

   I really appreciate all the responses.  To clarify my original post, I am looking to make an exact image of my drive.  Reason being that I'm new to Linux and in the event that a pooch my drive doing something stupid, that I would be able to just copy an image back and have everything the way it was before.  It took a huge amount of time to get this the way I want it (including VMs and stuff) but I am finaly able to remove my dual boot.  Hence, if I break it I would like a sure fire way to restore it.  I don't need the empty space backed up, but if that's the only option then so be it, I can live with that!  So now where does that leave me?  Thanks again for all your help, it is so greatly appreciated!!

---

### Post by bumanie on 2008-12-03
I guess it comes down to what one interprets as a full drive image - I interpret that as OS, free space and everything else (programs etc.). It is really up to you to decide what you want. It may be worth looking at what scorp123 suggested with > copying just the files, either using "rsync" or putting them into "tar" archives. As it sounds as though you would prefer not to have the free space imaged/cloned. Do a bit of reading and get back to the forum and someone will help with what you decice to do.

---

### Post by fishman78 on 2008-12-03
> **bumanie said:**
> I guess it comes down to what one interprets as a full drive image - I interpret that as OS, free space and everything else (programs etc.). It is really up to you to decide what you want. It may be worth looking at what scorp123 suggested with As it sounds as though you would prefer not to have the free space imaged/cloned. Do a bit of reading and get back to the forum and someone will help with what you decice to do.

I am mainly interested in ease of use and reliablility.  If I have to spend and extra 50 on HDD space for something that works then it's money well spent IMO.  Sounds like doing a complete (empty space included) image is the easist after doing some reading, but man, there's a lot of material on this subject :D

---

### Post by Duck2006 on 2008-12-03
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by gjoellee on 2008-12-03
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

this is software uses GUI and is very easy to use, you can make backups and ISO images

---

### Post by scorp123 on 2008-12-03
> **fishman78 said:**
> man, there's a lot of material on this subject :D You can ask 6 UNIX admins the same question ... and you will get like 20 answers. **All of them correct.** :D

Here on UNIX-like operating systems such as Linux there is always more than one correct way to do something. Especially backups ;)

---

