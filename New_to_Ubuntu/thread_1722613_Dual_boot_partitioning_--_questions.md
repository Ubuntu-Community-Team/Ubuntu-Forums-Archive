---
title: "Dual boot partitioning -- questions"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-06
[FONT=Times New Roman]Now that I was finally able to get my new 560 Gb SATA drive to work as the boot disk on my old system, which I am rebuilding, and was subsequently able to successfully install Windows XP with SP3, I am now ready to set up the dual boot system using Ubuntu 10.4. I have read several articles on how to partition the drive, with all of them recommending doing it manually, but they all suggest different approaches. I must say that I am rather confused and somewhat intimidated. I have not installed any software yet on the Windows partition, but have setup the Internet. As I do not want have to use antivirus software, I would prefer to get Ubuntu installed immediately so I can access the Internet via Linux. Here is what I think I should be doing: Shrinking the Windows partition down in size, creating a root partition for Ubuntu, creating a home partition for Ubuntu, and also a swap partition. I am not sure where Windows and Ubuntu share space for files or if that is even necessary, nor am I sure what size these various partitions should be made or what kind --- real or logical. If I could be directed to a set of **implicit instructions** for a novice computer builder it would be a tremendous help. Thank you :confused: [/FONT]

---

### Post by bodhi.zazen on 2011-04-06
The tools to do all this are included on the Ubuntu desktop CD.

There is more then one way to skin the cat and it is more important that you understand how Linux refers to partitions then which method you use.

Personally what I do is to use gparted to shrink the windows partition.

Then I start the installer and install Ubuntu into the free space.

In general you need a swap and a root partition. IMO swap should be the size of your RAM X 2, max 1 Gb.

You will then need at least 5 Gb for root, and I would advise 10-15 Gb.

Many people also use an additional partition for /home (user data is installed in home) or you may wish to make a shared data partition (ntfs would be a good choice) to share data from Ubuntu to Windows.

See also:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Again , there is no single method , you can achieve installation via several paths.

You can resize your partitions later if you make a mistake.

---

### Post by Hedgehog1 on 2011-04-06
Here is one way.

**[SIZE="4"]Defrag your Windows partition first.[/SIZE]**

The XP disk utility does not allow you to 'shrink' the windows partition (Vista and Win7 do), so you have to do it using gparted.

Boot from your Ubuntu LiveCD/LiveUSB.  Select 'TRY'.

Menu to system >> Administration >> Gparted Partition Editor

Right click on the NTFS partition, and select move/resize.  resize the partition to leave as much space as you want for Ubuntu (50 gigs, or 100 gigs or 200 gigs..)

**Given the size of your drive, I would suggest 100 gigs open space.**

Press the 'check mark' button to make the change real.


Right click on the empty space, and create an extended partition to the end of the disk.

Press the 'check mark' button to make the change real.


**/dev/sda5:** Right click on the empty space, and create a logical partiton, type EXT4 about 20-25 gigs. this will be your '/' (root) partiton.

Press the 'check mark' button to make the change real.


**/dev/sda6:** Right click on the empty space, and create a logical partiton, type Linux Swap. Make it the size of your RAM + 10%

Press the 'check mark' button to make the change real.


**/dev/sda7:** Right click on the empty space, and create a logical partiton, type EXT4  and use all the space left. this will be your '/home' partiton.

Press the 'check mark' button to make the change real.


[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-06
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

---

### Post by TCMGO on 2011-04-12
[COLOR=black][FONT=Verdana]Thank you....very much. Though I had major problems with my CD-ROM drive intermittently freezing up, for which I could never figure out, I eventually got Ubuntu installed. The dual boot function works fine. Now unto getting everything to work.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]:p[/FONT][/COLOR]

---

### Post by jbodden6977 on 2011-05-02
This is very frustrating and alarming to me. Ok I am a beginner and I believe in the tenets of linux - but i want ot keep my windows 7 (previous software investments) and all of the so called instructions have the following faults in them.
1) the 'teacher' assumes the student already knows what many things are, what the mean and how they are dealt with. Wrong, stupid stupid teacher...
2) many of the step by step with screen caps for illustration show things that to me, simply DO NOT EXIST!
WHY? damned if I know, and damned if I don't because when i encounter a goto and dothis that isn'there and doesn'twork... well I hit a brick wall.
OK, I used Win 7 to shrink my partition as per instructions of one who professed to know. Later I find another teacher who says ALWAYS USE GPARTED for those functions.
3) a lot of things written for BEGINNERS tell the beginner to do something - and then neglect to point out HOW and WHY those things are accomplished or need to be done.

Can anyone recommend to me a DETAILED and comprehensive guide for a total linux newbie, FOR dual install of win 7 (already in) and Ubuntu (as coexistent os)?
One that does not include OUTDATED REFERENCES TO PREVIOUS VERSIONS, AND SCREENSHOTS THAT LOOK (FROM PREVIOUS VERSIONS) NOTHING LIKE ANYTHING I CAN FIND ON MY MACHINE!:confused: [EMAIL="josephbodden@yahoo.com"]josephbodden@yahoo.com[/EMAIL]
Oh as a couple of examples - freed up space, created primary partition in freed space, get error NO ROOT SYSTEM DEFINED (something like) and even after looking up such examples of root system designations such as '/home' - it gets rejected and i get same error over and over.
yes i assigned the boot to dev/sda (already there as a default). More later.

---

### Post by muteXe on 2011-05-02
Hi jbodden6977,
Here's what I do, if i was you.
1. Lose the attitude.
2. Don't hijack another thread. Create your own.
3. In your new thread, post some useful stuff, like some of your hardware, current version of ubuntu you're using, stuff like that.
4. Be a bit clearer on what's actually wrong. Personally, I don't completely understand what you mean by:
> 
Oh as a couple of examples - freed up space, created primary partition in freed space, get error NO ROOT SYSTEM DEFINED (something like) and even after looking up such examples of root system designations such as '/home' - it gets rejected and i get same error over and over.

actually means. What steps did you follow to actually get these "error messages"?

Oh, and welcome to the forums.

---

### Post by bodhi.zazen on 2011-05-02
> **jbodden6977 said:**
> This is very frustrating and alarming to me. Ok I am a beginner and I believe in the tenets of linux - but i want ot keep my windows 7 (previous software investments) and all of the so called instructions have the following faults in them.
1) the 'teacher' assumes the student already knows what many things are, what the mean and how they are dealt with. Wrong, stupid stupid teacher...
2) many of the step by step with screen caps for illustration show things that to me, simply DO NOT EXIST!
WHY? damned if I know, and damned if I don't because when i encounter a goto and dothis that isn'there and doesn'twork... well I hit a brick wall.
OK, I used Win 7 to shrink my partition as per instructions of one who professed to know. Later I find another teacher who says ALWAYS USE GPARTED for those functions.
3) a lot of things written for BEGINNERS tell the beginner to do something - and then neglect to point out HOW and WHY those things are accomplished or need to be done.

Can anyone recommend to me a DETAILED and comprehensive guide for a total linux newbie, FOR dual install of win 7 (already in) and Ubuntu (as coexistent os)?
One that does not include OUTDATED REFERENCES TO PREVIOUS VERSIONS, AND SCREENSHOTS THAT LOOK (FROM PREVIOUS VERSIONS) NOTHING LIKE ANYTHING I CAN FIND ON MY MACHINE!:confused: [EMAIL="josephbodden@yahoo.com"]josephbodden@yahoo.com[/EMAIL]
Oh as a couple of examples - freed up space, created primary partition in freed space, get error NO ROOT SYSTEM DEFINED (something like) and even after looking up such examples of root system designations such as '/home' - it gets rejected and i get same error over and over.
yes i assigned the boot to dev/sda (already there as a default). More later.

Tons of install guides:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

If you find all that too difficult , why not try wubi ?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Other then that, I can see you are frustrated, but I can not tell what you want. First you ask for detailed guides, then you ask for screenshots ?

Guides get as detailed as you want and screenshots vary.

Other options you might have would be to see if there is a LUG (Linux Users Group) near you.

If you have a specific question at a specific step of the install, say you do not understand Linux partition schemes, ask.

---

### Post by panchocanti on 2011-05-02
Sorry guys to interrupt your post. I'm very new at Ubuntu. I'm starting to use last weekend thru Wubi installation. Really simple. 
My question, is there a decrease in performance installing Ubuntu thru wubi ??? I'm getting use to 11.04.
Regards,

---

### Post by bodhi.zazen on 2011-05-02
> **panchocanti said:**
> Sorry guys to interrupt your post. I'm very new at Ubuntu. I'm starting to use last weekend thru Wubi installation. Really simple. 
My question, is there a decrease in performance installing Ubuntu thru wubi ??? I'm getting use to 11.04.
Regards,

There may be a small performance hit you could measure with benchmarking, but, assuming you have anything resembling modern hardware you will not notice a difference with a standard install.

---

### Post by panchocanti on 2011-05-03
Thanks bodhi.zazen ¡¡¡¡ Tonight I will look for a benchmark app. Regards,

---

