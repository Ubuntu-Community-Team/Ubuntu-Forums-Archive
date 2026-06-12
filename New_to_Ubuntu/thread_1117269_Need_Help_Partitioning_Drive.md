---
title: "Need Help Partitioning Drive"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by tklaus on 2009-04-05
I am reinstalling Ubuntu because it crashed and I haven't been able to fix it. I want to reinstall it over the old one, but I went to do it and I can't install from the guided option. I am assuming I need to do the manual install but I don't know which partition is Ubuntu and which is Vista. One says sda1 and is 5% of the drive and the other is sda2 and is 95% of the drive. I would assume the larger one would be vista, but I am not sure because when I installed Ubuntu it basically did it for me. Also, wouldn't I need another partition for swap? I don't think I had this partition earlier so I am confused about that. Thanks for the help!

---

### Post by taurus on 2009-04-05
If you are not sure which is which, open a terminal and run this command.  The partition with ext3 filesystem is the one you want to install on.  Your windows should be ntfs and there should be another partition for swap so you do not need to create another one.

```
sudo fdisk -l
```

---

### Post by tklaus on 2009-04-05
I can't get to a terminal window because I can't boot Ubuntu. I think I might have set up the dual boot through wubi, so if I did does that mean my drive is not partitioned? I was wondering if I had done that and looked to see if I could uninstall Ubuntu then reinstall it but I could not find it in Vista.

Also, both of the partitions say ntfs but I don't know if that means anything. Sorry I am a real noob when it comes to this.

Actually I am almost positive I installed using Wubi. Is it more stable to do it with partitions?

---

### Post by taurus on 2009-04-05
I am talking about a terminal from Ubuntu LiveCD.  But if you installed it using wubi, then there is nothing to partition.

---

### Post by tklaus on 2009-04-05
Oh ok. I am didn't know that was what you meant. Is wubi far inferior to actually partitioning the drive? I thought this is what I had done but I guess not. If I did not use wubi then there shouldn't be any ubuntu files in windows right? I read that wubi has a little lower performance but is it that drastic of a difference? Thanks.

---

### Post by taurus on 2009-04-05
Wubi is for those who want to test drive Ubuntu without resizing their harddrive.

---

### Post by tklaus on 2009-04-05
So is resizing one's hard drive a lot more stable than wubi? Because the problem came from when I let my battery die on my laptop while running Ubuntu and now it will not boot. Would you recommend actually partitioning the drive? Sorry I am asking so many questions.

---

### Post by taurus on 2009-04-05
Yes, I would definitely recommend you install Ubuntu on it own partition instead of through windows.  Of course, you need to resize your harddrive unless you want the installer to do that for you but _back up_ your personal files first just in case.

Don't forget to defrag your harddrive (from windows) a couple of times first.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by presence1960 on 2009-04-05
> **taurus said:**
> Yes, I would definitely recommend you install Ubuntu on it own partition instead of through windows.  Of course, you need to resize your harddrive unless you want the installer to do that for you but _back up_ your personal files first just in case.

Don't forget to defrag your harddrive (from windows) a couple of times first.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[SIZE="7"]+1[/SIZE]

Here is a partitioning guide : [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by raymondh on 2009-04-05
> **taurus said:**
> 

Don't forget to defrag your harddrive (from windows) a couple of times first.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Very, very important.  

Good luck.

---

### Post by tklaus on 2009-04-05
Ok I am going to partition. I already shrunk the vista partition so I freed up about 50 gb to use for ubuntu. Is that too much? Also, if I go through the install do I just choose the guided option and it will set up the swap and the other file I need automatically? I haven't defragged yet so was I supposed to do that before I shrunk the partition?

I defragged yesterday but I am defragging again. It's only doing it to the 100 gb or so that makes up the vista partition. Should I change it back so it can defrag the whole thing?

---

### Post by Sef on 2009-04-05
>  Also, both of the partitions say ntfs but I don't know if that means anything. Sorry I am a real noob when it comes to this.

If you installed Wubi, then the NTFS partitions are fine.   When you install Ubuntu on your system, you need to use a different file system.   The default for Ubuntu is ext3 which works just fine.

---

### Post by tklaus on 2009-04-05
Ok. So if I just delete the wubi/ubuntu files from the C folder in Vista do I need to do anything else to get rid of it? I can't do the normal uninstall option because it is messed up. Also, I think this is what you were saying, but if I just do the guided installation it sets up the ext3 partition and the swap partition automatically right? Or should I do it manually? I really appreciate your help you guys. I know I am asking a lot of dumb questions.

---

### Post by Didius Falco on 2009-04-05
I'd recommend using Revo Uninstaller in Windows. It does a great job of completely uninstalling things from Windows, and will even work on broken uninstalls.

The best part is there is  a portable version, so you can run it from a USB stick or just put all the files in the same folder - no registry entries, dlls added to System, etc.

Oh yeah - it's freeware too...

Here is a link: [http://www.revouninstaller.com/revo_uninstaller_free_download.html](http://www.revouninstaller.com/revo_uninstaller_free_download.html)

---

### Post by tklaus on 2009-04-05
Thanks for the uninstaller thing. I opened it and it looks like it works pretty well. The only problem I am having is that Wubi/Ubuntu is not appearing there or in my add/remove programs. I tried searching too and it doesn't work, but I can see the files in my C folder.

---

### Post by -kg- on 2009-04-05
> **tklaus said:**
> Ok I am going to partition. I already shrunk the vista partition so I freed up about 50 gb to use for ubuntu. Is that too much? Also, if I go through the install do I just choose the guided option and it will set up the swap and the other file I need automatically? I haven't defragged yet so was I supposed to do that before I shrunk the partition?

I defragged yesterday but I am defragging again. It's only doing it to the 100 gb or so that makes up the vista partition. Should I change it back so it can defrag the whole thing?

I would say that 50 GB is fine for Ubuntu.  And yes, you should have defragged the Vista partition *before* you shrank it, but if you did it with Vista's partitioning tool, it'll likely be OK.  Can you still boot into it right?  If so, it wasn't hurt. (Big chance, though!)

Also, if your Vista partition is 100 GB, that's what you want.  Unless you have another ntfs partition (with data or files on it that you intend to shrink), that's the only one you need to defrag.  Defrag is absolutely necessary for Windows partitions which you need to shrink to a smaller size.

If you don't intend on shrinking or moving a partition, it isn't necessary to defrag those in preparation for a Partitioning operation. And if you've already shrank the partition, it isn't necessary for installing Ubuntu, unless the installer *insists* on resizing it.

> Also, I think this is what you were saying, but if I just do the guided installation it sets up the ext3 partition and the swap partition automatically right? Or should I do it manually?

Yes, exactly right.

I don't know if you are installing 8.04 or what, and I have heard different things, but you should be presented with 3 options for partitioning:

1. Guided Install - Use Whole Disk: **_Don't use this one,_** it will use the entire hard drive and wipe out all other partitions on the drive, including your Windows partition.

2. Guided Install - Resize Partitions: You could use this, but it shouldn't be necessary (unless the only other option) because you have already cleared some free space.

3. Guided Install - Use Largest Contiguous Free Space:  **_This is the one you want._**  You have already cleared 50 GB, which should be more than enough for an Ubuntu installation.

4. Manual Partitioning - Not necessary to use this unless you just want to do it manually to, say, set up a separate /home partition, or others.

I don't know if the Live CD Installer for previous versions of Ubuntu have all these options, and I would hope that subsequent versions would keep them, but that is what I was presented when installing 8.04 Hardy.

Do check out the Community Page that Presence suggested.  I was it's most recent re-writer and editor.

---

### Post by tklaus on 2009-04-06
Thanks KG.

All of those options are available, however the "use largest free space" did not select the open 50 gb but the whole thing. I think it is because I did not designate the type of partition (like ntfs or fat32). Is that probably why?

As far as the defragging goes, if I had done it the day before I resized would I have been ok?

---

### Post by -kg- on 2009-04-06
> **tklaus said:**
> Thanks KG.

All of those options are available, however the "use largest free space" did not select the open 50 gb but the whole thing. I think it is because I did not designate the type of partition (like ntfs or fat32). Is that probably why?

I wouldn't think so.  The guided install *should* default to ext3, and it should create a sufficient swap partition, as well.  Not seeing what is going on is a problem.  Is there a way that you can snap a screen shot of the point where you say it is selecting the entire drive?  It shouldn't be doing that, not with Guided - Largest Contiguous.  Also, did you make sure you clicked the proper radio button at the selection screen?

> **tklaus said:**
> As far as the defragging goes, if I had done it the day before I resized would I have been ok?

If you can still boot into Windows, you're OK at any rate.  Defragging before the partition operation would have just made it safer and had less potential for problems from the partitioning operation(s).

Along with defragging the files on the partition, defragging also tends to move files toward the beginning of the partition (the left side on the graphics).  This means that there are few (or ideally, no) files to the right, where most of the operations are performed; specifically, shrinking the partition.  Less files to move means less risk that they will be miscopied by the partition editor and a quicker partitioning operation to boot.  Less files to move = less time.

But if you have successfully shrank the partition and there are no problems with it, then that should be it and it should not affect the installation process.  Like I said, it *shouldn't* be selecting the whole drive under the Guided Install you're trying to use.

You might have to do the manual install, select the free area, specify sizes for your partitions, mark them ( "/" (that's root) and "swap") and install from there.  Same difference, just more work.  Swap should be 1.5 X Amount of RAM and your ext3 partition should encompass the remaining space.  With 50 GB free, this still should be adequate.

Try again with the "Largest Contiguous" selection and get some screenshots if you can.  You should be able to do that if you boot to the Live CD, then click on the Install icon.  You will get all the screens you need for the install, and you should be able to get into the regular Ubuntu menu system as well.  The snapshot tool is under "Applications/Accessories/Take Screenshot" (I assume you are installing Ubuntu and not Kubuntu or Xubuntu here).  You should be able to take a screenshot and save it or send it in an email.

If you just can't get it to work right, I or someone here will walk you through the manual partitioning operation.  That's the method that I used to install on all my computers because I wanted a separate /home partition and because I'm very, very comfortable with partitioning operations.  I've done them for quite a few years on quite a few computers and even more hard drives (I have and have had multiple hard drives in most of my recent computers...recent = the last 15 years or better). ;)

---

### Post by tklaus on 2009-04-06
I ended up doing a manual partition because the guided one still was selecting the whole hard drive for the free space option. I did the ext3 for root and I did 2 gb for the swap file. I couldn't make a home partition because I have a vista partition and some recovery partition that I think sends everything back to factory default. I appreciate your help and I am actually using the newly installed Ubuntu right now! I did check to see if windows would still boot and it did so I think I am in the clear now. Thanks again!

---

### Post by taurus on 2009-04-06
Sounds like you've hit the 4 primary partitions limitation.  Therefore, you couldn't create another partition unless you make one of those 4 primaries to an extended partition, then you can create more partitions (logical) under that extended partition.

---

### Post by Didius Falco on 2009-04-06
tklaus,

How did you go with getting rid of the Wubi install? You should take a look at this Wiki page for instructions on manually uninstalling  Wubi from Windows: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

Enjoy!

---

### Post by raymondh on 2009-04-08
> **taurus said:**
> Sounds like you've hit the 4 primary partitions limitation.  Therefore, you couldn't create another partition unless you make one of those 4 primaries to an extended partition, then you can create more partitions (logical) under that extended partition.

Yup .... +1

Ahhh, the magic of the EXTENDED partition :)

Raymond

---

