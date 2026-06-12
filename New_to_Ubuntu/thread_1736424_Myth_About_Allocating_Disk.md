---
title: "Myth About Allocating Disk"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by thaliakasih on 2011-04-22
Hello all.
I am a girl who wants to try Ubuntu Linux.
My level of education is still in high school (year 1) and had been and still continue using Windows.
I had just downloaded Ubuntu and am typing this thread using Ubuntu Test.
I rated myself as a bit above average user of people my age.
(I told you all this so that you could help me in my level of understanding :))

Okay so here it is.
When I was doing the installation, everything went fine till Ubuntu asked me to allocate my disk.
There were 3 option:
- Install alongside other OS
- Install using all disk.
- Customized.

My questions are:
1. If I try the first option, do I have to be a root to access Windows partition ?
2. If I try the 3rd option, should I allocate swap as swap=2*RAM? Many people talk about this on internet but never tell the reason. I have 6 GB RAM and 750GB (only allocate about 100-250GB or less to Ubuntu, though). Should I allocate 12 GB for swap? Is it necessary? Why?
Note: I want my computer to be powerful because I'm going to try heavy softwares, like software similar to AutoCAD, Wine, games etc.
3. What Allocating Space strategy would you guys recommend with 6GB Ram, 100-250GB HDD?
4. What is Keyring? When I set password to my wireless, keyring-thing pop up. Asked me for password again. FEEDBACK for Ubuntu developer: It would be nice if for every pop up like that, there are link or short explanation so users wont get wrong information when search about it. Talk about user-friendly.
5. Initially my wireless and Nvidia GT 540M were not detected. When I clicked System -> Administration -> Additional Drivers,  there was something called proprietary driver and Ubuntu cannot improve or fix the driver. Will this reduce of my internet speed? Is that means in normal circumstances, Ubuntu developer make the driver?
6. What CAD software do you guys use in Ubuntu? Please recommend a good one.
7. Does Ubuntu has a software to make a very big desktop when we drag the  mouse it will take move the desktop (like scrollbar). I want to improve my productivity, like looking at pdf file and typing in office just by moving the cursor without clicking the tabs anymore

Sorry for long list of questions. Please free to respond even for only part of the question.
Cheers.

---

### Post by Bucky Ball on 2011-04-22
Welcome. 10.04 LTS is best for stability (essential if you're in school!).

Go the third option, manual partitioning, and just leave the Windows partition alone. You will see it there, NTFS partition. This way you have a separate /home partition, method 1 & 2 you don't. This is handy to have for a lot of reasons. Create, in this order:

/ = root partition, OS. 20Gb plenty.
/home = your settings and data; music, vid, etc; big as you like leaving enough free space at the end for ...
/swap = I would go the size of your RAM but check this if you are intending to hibernate. The old rule used to be double the RAM if you're intending to hibernate. Not sure if that's still applicable.

These three partition names are defaults in the partitioner so all you need to do is choose them and size them. You can have custom ones like /sockcollection if you want also. Choose the filetype EXT4 for the partitions.

If you are running from the LiveCD, wireless is going to be problematic. If you still have problems with a full install it should be fixed easily if you have it running at all at this point. Same with your vid. There is nowhere to actually install the additional drivers, if you follow, as you are running from the CD. ;)

Not much I know of that matches pro CAD, but that's only what I've read. There are plenty of users into it who can give you some clues there.

Not sure about question 7. 

Hope that's some help. Have fun with it, enjoy the learning curve, and good luck. Once you're set up it's worth the effort (if it does what you need and you like it, of course!).

PS: This site's always been my favourite for dual-booting info. Should help:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

PPS: When you have finished installing and are at the desktop, plug in an ethernet cable. You will be advised that you have updates; get them and see if you are offered additional drivers/firmware. Ubuntu runs faster with a hard drive install, incidentally, but you probably guessed that!

---

### Post by xachu4u on 2011-04-22
which ubuntu version are u installing? As per my knowledge. there is supposed to be another option: install ubuntu in the longest free-space available. that would be a good option...

---

### Post by TeoBigusGeekus on 2011-04-22
Proprietary drivers are drivers that are developed by other companies than Canonical (which creates Ubuntu). They are closed source, therefore ubuntu cannot intervene with them (improve of fix them). Hardware generally tends to work better with them.


If you're serious about CAD, then there's nothing equivalent to Autocad in linux.
If you just want it for drafting and 2d design, there is Bricscad, Draftsight and Qcad (some of the not totally shitty ones).

---

### Post by Blasphemist on 2011-04-22
Wecome taliakasih! I'd consider you above average for any age considering your questions. I'll take a shot at some of the questions and leave out those like about CAD since I don't use that.

1. and 2. You'll have access to the windows partition to read files if you install taking that option and install as you describe that you desire. That option will shrink the windows partition to create room for Ubuntu but won't give you control of the Ubuntu partition size. It will create an appropriate swap partition based on your memory. BTW, swap just needs to be a bit larger than RAM. With the amount of RAM that you have swap will be used very little other than for hibernation.

3. If you use custom, you can choose your partitioning. The sizes you describe look good but there are these main variables. If you leave too much to windows, and then want to store a huge number of pictures or a lot of music or anything else that requires a lot of storage, you could end up wasting a lot of space by having given it to windows now. No matter how much I defrag Win 7, I have trouble getting any more space for Ubuntu. Until Kaspersky runs out I'm stuck. Then I'm going to kill windows and go all Linux. I would create a partition for home. Look at this link that shows doing that. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

4. I agree about the keyring but just trust that it will not continue to be an issue. I've been using the natty beta and had an issue with that but it is now solved for me at least. You'll have access to the keyring control.

5. Drivers are a deep subject and I won't try to explain it all here, and couldn't do it well if I tried. Open source drivers for many devices are built into the kernel and as new hardware is available that gets updated. The drivers included usually work fine and don't inhibit performance at all. Often hardware vendors don't create drivers for other than windows and maybe mac. Because of this there can be a lag between hardware use and open source drivers that take full advantage of that hardware. Ubuntu developers are just a part of the open source community that constantly updates for use of new and stronger hardware.

7. Yes, you can just move the mouse over an application and then scroll within that app in most cases. You have control over this behavior in Ubuntu. You'll also have multiple workspaces, a huge improvement from windows. You can use multiple monitors as well. You can have a bigger virtual display than physical but I personally feel there are better solutions than that in Ubuntu.

---

### Post by el_koraco on 2011-04-22
> **thaliakasih said:**
> 
My questions are:
1. If I try the first option, do I have to be a root to access Windows partition ?
2. If I try the 3rd option, should I allocate swap as swap=2*RAM? Many people talk about this on internet but never tell the reason. I have 6 GB RAM and 750GB (only allocate about 100-250GB or less to Ubuntu, though). Should I allocate 12 GB for swap? Is it necessary? Why?
Note: I want my computer to be powerful because I'm going to try heavy softwares, like software similar to AutoCAD, Wine, games etc.
3. What Allocating Space strategy would you guys recommend with 6GB Ram, 100-250GB HDD?
4. What is Keyring? When I set password to my wireless, keyring-thing pop up. Asked me for password again. FEEDBACK for Ubuntu developer: It would be nice if for every pop up like that, there are link or short explanation so users wont get wrong information when search about it. Talk about user-friendly.
5. Initially my wireless and Nvidia GT 540M were not detected. When I clicked System -> Administration -> Additional Drivers,  there was something called proprietary driver and Ubuntu cannot improve or fix the driver. Will this reduce of my internet speed? Is that means in normal circumstances, Ubuntu developer make the driver?
6. What CAD software do you guys use in Ubuntu? Please recommend a good one.
7. Does Ubuntu has a software to make a very big desktop when we drag the  mouse it will take move the desktop (like scrollbar). I want to improve my productivity, like looking at pdf file and typing in office just by moving the cursor without clicking the tabs anymore

Sorry for long list of questions. Please free to respond even for only part of the question.
Cheers.

1. If you use the install alongside option, you will get the option to shrink the Windows C: drive. How much space you will get to allocate to Ubuntu will depend on how big your C: drive in Windows is. Ubuntu will then be installed on an extended partition, with two logical partitions - root (/), and swap. 

2. The swap partition is used by the system in cases where the memory is exceeded. With 6 GB memory, you will probably not need it in such cases, although going without the swap partition might cause problems with suspending and hibernating. if you do decide to make it, 6-8 GB should be fine. 

Take note that when doing the manual partitioning, you will want to shrink the Windows partitions using the tools in Windows. i suggest you read up here: 

[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

3. See the tutorial. 

4. The gnome keyring is the most annoying piece of software when you first start using Ubuntu. It is a utility that encrypts the passwords you use, so that they can't be acessed or read. While this can be useful in some cases, it can also cause problems. There are two ways to get rid of it. 

a) Do not choose the automatic login option. 
b) When it pops out for the first time after you install Ubuntu, do not enter a password, just leave it blank and hit OK. It will then ask if you are sure. Click on the "Use unsafe storage" option. You will be grateful for that later on. 

With this, I fully see you frustration, I've had my share of trouble with the keyring. 

5. Some drivers for software are not made by the Linux kernel or by Ubuntu developers, but by the companies that produce the software. ubuntu includes the option of using those drivers, and in some cases it is necessary, as with the wireless drivers, but they generally don't reduce the system performance. It is always a gamble, though, and you just can't be sure until you've installed them. 

As for the CAD questions, what the Big Geek said. 

As for 7, i don't understand the question. 

General advice - take it one step at a time, and don't get discouraged. There is an initial learning curve, but once you start getting the hang of things, you'll get more in touch with the system. For any questions, there are always the forums.

---

### Post by Blasphemist on 2011-04-22
This screenshot is where the settings for question 7 are in natty.

---

