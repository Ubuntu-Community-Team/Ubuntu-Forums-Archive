---
title: "[SOLVED] Accidental sudo rm -rf /"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by intense.ego on 2008-12-31
I'm not sure whether this should go in the beginner's section or in the general help section, but I did something very noobish.

You see, I had a home backup on an external hard drive from a couple of months back when I was about to  install the new ubuntu. I was in need of space on my hard drive so I decided to move some files to my external hdd, but it was out of space too. So I decided to delete the backup since the install was running fine and the backup was no longer necessary. The thing was that when I tried deleting the folder, only about 2gb of data (out of 34) could be deleted at a time because of the limited size of the wastebasket (it can only be as big as the amount of free space available on the /home partition). This would have taken too long.

I couldn't figure out how to delete without sending to wastebasket first using the GUI, but then I remembered the command sudo rm -rf. I thought this was a perfect moment to make use of the terminal command.

So, I right clicked on the "homebackup" folder and selected "open terminal here." I then proceeded to type sudo rm -rf /* because I thought it would delete everything IN THE DIRECTORY I HAD GONE INTO (it turned out later that the command continues doing what it is supposed to, irrespective of the directory the terminal is in). I had my doubts when the terminal said something about "read-only permission" so I closed the terminal. The process seemed to continue, however, and there were some unexpected changes (file manager seemed to revert to a different style, firefox crashed, rhythmbox attempted playing 20 songs at once, etc - what you see in youtube videos about sudo rm -rf). I then decided to check and make sure I wasn't imagining this. I opened my home folder and saw that there was 3.7gb free as opposed to the 2.4gb free there was earlier. That is when I turned off my computer (manually, because the option in ubuntu was greyed out).

I tried rebooting, but GRUB came back with "Error 15." I need help. First of all, is there any way of knowing what files were deleted? (like a change log or something - or is the deleting in a random order) What will I have to do to return to normal or will I have to start everything afresh? If I have to start afresh, can I salvage some of my more important files?

Thanks in advance for your help and cooperation

---

### Post by SuperSonic4 on 2008-12-31
It's very likely you've lost everything essentially wiping your drive.

sudo = assume root
rm = remove
-rf = delete everything inside the directory and force it to go without asking for confirmation
/ = root folder, has everything in

If you need to delete /home/user do ```
rm -rv ~
``` which will show you what it does after asking for confirmation.

---

### Post by Michael.Godawski on 2008-12-31
hi and my sympathy

you can access your remaining files via the Live CD:

[http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)

and then I would reinstall.

---

### Post by nhasian on 2008-12-31
try testdisk.  boot off a liveCD install *testdisk* from the repos.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

TestDisk can

    * Fix partition table, recover deleted partition
    * Recover FAT32 boot sector from its backup
    * Rebuild FAT12/FAT16/FAT32 boot sector
    * Fix FAT tables
    * Rebuild NTFS boot sector
    * Recover NTFS boot sector from its backup
    * Fix MFT using MFT mirror
    * Locate ext2/ext3 Backup SuperBlock
    * Undelete files from FAT, NTFS and ext2 filesystem
    * Copy files from deleted FAT, NTFS and ext2/ext3 partitions. 

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery.

---

### Post by mikewhatever on 2008-12-31
I think there is no other option but to reinstall. Try recovering some of the files with photorec. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Edit: In oder to delete a file/folder without sending it to trash, highlight the items you wish deleted and hit shift+del.

---

### Post by louieb on 2008-12-31
> **nhasian said:**
> try testdisk. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)



> **mikewhatever said:**
> Try recovering some of the files with photorec. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
 

+1 to both.  Available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by intense.ego on 2008-12-31
Well, by the time I turned off my computer only 1.3 gb (from the home folder) seemed to have been deleted so is all still lost? Can I not still recover some word documents, etc if they were not deleted? Or does what was deleted render my hard drive unreadable? 

But either way, it looks like I'm going to have to reinstall. Does the fact that I had / and /home on different partitions change the situation in any way? As long as I can recover some more important documents, its not such a big loss. Thanks for your help so far, guys

---

### Post by Michael.Godawski on 2008-12-31
I guess you nuked your / partition so the root partition not your /home.

Try to access it via the guide I posted above.

---

### Post by mikewhatever on 2008-12-31
You may be able to recover all of your personal files. The fact that root and home are separate should make it easier. You'll probably want photorec to copy files from home to the external HDD, so make sure there is enough space there.

---

### Post by Dr Small on 2008-12-31
I wouldn't be so sure. The fact that he was running it for /* is enough to say that it can descend into /home and delete files also. At least, that is my assumption.

To the OP, my sympathy.
You may try booting from a LiveCD and attempt to recover that which is not deleted. After that, reinstall and pay a little more attention to your commands from now on. ;) Once, I deleted my /boot directory on total accident, and was able to rebuild it all without (totally) panicking and rebooting. (Must be a windows mindset to reboot in panic!)

Dr Small

---

### Post by handydan918 on 2008-12-31
To the contrary of the esteemed Dr. Small, i think you /home is probably intact. I recommend booting the live cd and getting those files out of there, before disaster strikes with greater accuracy. Back them up to an external drive, or a thimbie, or whatever. 
THEN try reinstalling, saving the existing /home partition.

Kinda smarts, don't it?

:P

---

### Post by intense.ego on 2009-01-01
Just out of curiosity, if, in fact, everything has been compromised, how would I go about recovering my files. You've tolde me which programs but in which order do I use them? What do they each do?

---

### Post by gn2 on 2009-01-01
Now if you had used GUI instead of terminal then you wouldn't be in this mess.... :rolleyes:

---

### Post by my_key on 2009-01-01
Do not write anything to that harddrive! Every byte written, means more lost files! Make an image of that partition using some sort of live cd and the dd command and save it to an external harddrive (this is optional, because you can work on the drive itself, but if you have the possibility it's safer to run these tools on an image). 

Then run photoreq or [some other file carving]("http://www.forensicswiki.org/wiki/Tools:Data_Recovery#Carving") utility on this. [Irongeek made a good video tutorial]("http://www.irongeek.com/i.php?page=videos/data-carving-with-photorec-to-retrieve-deleted-files-from-formatted-drives-for-forensics-and-disaster-recovery") about this. Make sure you don't forget to adjust the setting on what filetypes you want photoreq to recover. I 've used these tools to recover thousands of pictures, mp3s, ... on several people's computers, so not all is lost if you act quickly. I would not suggest on trying to recover your whole operating system. Go for a fresh install. With Ubuntu this only takes half an hour to an hour any way.

Good luck!

---

### Post by The Cog on 2009-01-01
If you had a separate /home partition, I would be inclined to go about a new install but choose custom partitioning. Install a new Ubuntu on what was the old / partition, and choose to use your /home partition as /home again, but choose not to re-format it. Any files that remained in /home when you killed the rm process will still be there. 

Good luck.
I guess you don't need a lecture about keeping backups right now.

Edit:
I hadn't heard about photoreq. If it can do what they claim, then what my_key says is a good approach, and a re-install could overwrite info you need.

---

### Post by my_key on 2009-01-01
Oh, and check the photorec wiki.

e.g. [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by Dedoimedo on 2009-01-01
Not only did you nicely wipe important bits of your OS, you also nicely rounded it off with a shutdown, to make sure things are harder to recover :)

I would reinstall from scratch. Sure easier and less complicated than fixing the mess. And if you have backups, then it's a very valuable lesson.

Dedoimedo

---

### Post by intense.ego on 2009-01-01
> **Dedoimedo said:**
> Not only did you nicely wipe important bits of your OS, you also nicely rounded it off with a shutdown, to make sure things are harder to recover :)

I would reinstall from scratch. Sure easier and less complicated than fixing the mess. And if you have backups, then it's a very valuable lesson.

Dedoimedo

I know I shouldn't have shut down, but I panicked and I didn't know what else to do. Well, you live and you learn. From now on, I'm getting my computer to backup every night. 


Let me know if I'm understanding correctly. I should go about things like this:

1)Boot off a live cd and install photorec
2) use the dd command (what is it?) and make an image of the drive
3) use photorec or just copy and paste files from /home to salvage whatever I can and need
4) fresh install everything, both / and /home

---

### Post by intense.ego on 2009-01-01
Okay, I've decided to just save as many files as I can and then do a complete reformat. Ubuntu makes it relatively easy to know which files are lost - they are unreadable and an X is present on their icons. I do have a problem, though. I have a virtual machine that's 10gb in size and its still in tact. Moving it is a problem, however, because my external HDD is in FAT16 and does not support files greater than 4gb. Is there a way of getting it off safely? I'm thinking of compressing it into .rar s but is it possible to do it so that they automatically move onto the external hard drive without having to go through the internal HDD first?

---

### Post by my_key on 2009-01-01
dd is a command to make an exact image of a drive. It copies everything. Even files your OS considers bad or or non-existing. You use it in such a manner:

```
dd if=/source of=/destination
```

*if* is the input file, in your case you would choose your hard drive (everything is a file in unix, so is your harddrive), and *of* the file to which it writes the output.

To backup your first hardrive to an external usb drive make sure the first harddrive is unmounted and type:

```
dd if=/dev/sda of=/media/externalusbdrivesname/backupfirstharddrive.img
```

If you have a separate home partition which you know is hda4 an you only wish to recover that, feel free to change to "if=/dev/sda4". The  conv=noerror,sync option makes sure any errors dd encounters will result in the remainder of the block being replaced with zero-bytes. 

Then there's only one more thing you should currently know about dd and that is blocksize.

```
dd if=/dev/sda of=/media/externalusbdrivesname/backupfirstharddrive.img conv=noerror,sync bs=4k

```
The larger the block size, the quicker dd will copy, but each time dd encounters an error, the remainder of the block is ignored. Small block size ensures less data loss and vice versa. But copying with a smaller block size is more time consuming. So there's a time-data trade-off.  

Default blocksize is 512, since you just deleted everything I don't expect you to have a damaged hard drive. So setting it to 4k (4OOO) will speed it up quite nicely. If you do get lots of errors [dd_rescue]("http://wiki.linuxquestions.org/wiki/Dd_rescue") might be a better (faster) way to go, but I didn't suggest it since you don't have a damaged hard drive, you just accidentally hosed all the files.

For yet more info see: [http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

---

### Post by my_key on 2009-01-01
If [this]("http://ubuntuforums.org/showpost.php?p=4267888&postcount=3") is right, than just replace "foo.rar" by /media/externalharddrive/foo.rar 

This should do the trick.

---

### Post by my_key on 2009-01-01
Or even better, because using free software, is what's suggested in [this tread]("http://www.linuxquestions.org/questions/linux-software-2/tar-split-question-605013/"). But replace "/name/of/archive.tar.bz2" with /media/externalharddrive/backupvirtualos.tar.bz2

They give several pointers for unpacking also...

---

### Post by scorp123 on 2009-01-01
> **handydan918 said:**
> To the contrary of the esteemed Dr. Small, i think you /home is probably intact. And why do you assume that? This part ... ```
/*
``` ... is pretty clear and means what it means:  "everything underneath /" which includes /home as well. 

When I was a noob I did the absolutely same mistake ... /usr, /sbin and /etc were gone in a split-second, before I could hit Ctrl+C .... Ext2 was really fast back then :twisted: (1996).

---

### Post by intense.ego on 2009-01-02
I decided to install Ubuntu, but I've run into some trouble. If you guys could help, here is the thread I created: [http://ubuntuforums.org/showthread.php?p=6479346](http://ubuntuforums.org/showthread.php?p=6479346)

---

