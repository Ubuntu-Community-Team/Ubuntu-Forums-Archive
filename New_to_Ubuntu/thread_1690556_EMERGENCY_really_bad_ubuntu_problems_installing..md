---
title: "EMERGENCY: really bad ubuntu problems installing."
date: 2011-02-18
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-02-18
Right, I have been having many many problems with ubuntu installing on my laptop, I will explain below and any help would be appreciated in its extremity.

Right, when I try to install ubuntu, I am having problems with the partitions, I installed ubuntu on my other computer and it gave me three options for the partitioning and it gives me a slider so I can dual boot with windows 7, but it is now impossible to do on my laptop because the options for the slider isn't there and I have to do a partition manually, which is extremely complex, and it also says the main 320gb hard disks content is 'unknown' and I can't make a partition because it won't let me. so I log onto windows and make about 50GB free space, choose ext4 when installing and choose / out of the boot option and when I try installing it, click on the time zone it says the CD is damaged or cd drive and needs cleaning fluid or something, I have burned twice and then ordered a disc, so this is not a problem.


It also says when I put the CD in and click esc when it is loading it says dev, line 7 can't be found or something on the command prompt screen.

HELP! 
Thank you!!

---

### Post by dpwilson on 2011-02-18
Perhaps your live cd or what your installing from is corrupt.  Have you tried using another disk?

---

### Post by vacco on 2011-02-18
He already stated that he has tried 3 discs.

What options do you you have for partitioning now, and how is your hard drive partitioned?

---

### Post by vnpifhf on 2011-02-18
well I have a 320GB hard drive, which ubuntu states I've used 'unknown' meaning I can't partition it.
so I log on to win 7 and split 50gb into free space, go back to ubuntu and use it at a partition and set it as a ext4 and use a / thing as a boot? not sure, but basically It does not give me a slider option, and then after it works (sometimes) I click on the time zone and set it to london, fill the username area but it does not give me the forward option and it stalls and says the cd is corrupt or cd drive and it needs cleaning or something? then it gives me the desktop running off the CD.

---

### Post by restorator on 2011-02-18
Perhaps it's not the CD's that are bad but the CD drive itself is failing.

---

### Post by janthonywj on 2011-02-18
I'm no guru, but have you tried booting to a gParted CD and partitioning space out that way? I don't know for sure, but I wouldn't think booting to Windows and creating a partition would be optimal for creating a Ubuntu partition. 

I would also suggest ditching Windows 7 as your main OS... and run it in a VM when you have to... :P

The whole CD drive needing cleaning thing is weird, I've never heard of anything like that. Since the very first time I installed linux I have always created partitions manually, and it's not complex at all. I suggest doing so. In the simplest form, create a primary partition of about 15GB to 30GB (TONS of space, may be overkill for you) and format it ext4 with a '/' (root) section, then the equal amount of space as you have RAM and set it to swap, then the remainder of space set to /home for all your files and such. 

Doing this means you can jump around from distro to distro and experiment without touching your files. I can go try KDE for a week or two without having to back up my music and photos and such. When you become more experienced you can try out some of the other file systems offered, and maybe create other partitions for /opt and /etc and such so you can more easily carry installed software with you.

---

### Post by oldfred on 2011-02-18
Most win7 portables have used all 4 primary partitions leaving no space to install. You have to delete one primary to convert it to an extended which can hold many logical partitions which Ubuntu will use.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

---

### Post by vnpifhf on 2011-02-18
Ok, maybe what you are suggesting is right, but, why does ubuntu recognise the drive as unknown? because I can easily do this in ubuntu, and have done before many many times, because the place I work in uses ubuntu 9.10 and Edbuntu, but in this 10,10 its killing me, I will add some screenshots below;

I know I do not have a faulty CD drive because the laptop is new and Sony have checked it over.

---

### Post by arpanaut on 2011-02-18
Don't use capital letter in username   Known bug
You may need to convert sda4 to an extended partition before you continue.
The Installer should take care of that though.
I think it's the Caps in username

HTH

---

### Post by oldfred on 2011-02-18
The unknown is that it does not mount the NTFS partition to see how much is used. It may be that the partition needs chkdsk. Ubuntu & gparted usually do not mount NTFS partitions needing chkdsk to prevent further damage that then chkdsk could not fix.

arpanaut is correct that your name cannot be Jay but must be jay.

You should create sda4 as the extended partition so you can add both root & swap. Otherwise you are trapped with only 4 partitions.

---

### Post by vnpifhf on 2011-02-18
well I put jay and the same thing happened again, so that is clearly not the problem.
well I once typed in chkdsk in windows command prompt and then put in the CD because of another post with the same problem,
Sorry last poster I didn't understand most of that :/
Sorry mod!

---

### Post by 3602 on 2011-02-19
Why not just schwack the entire disk?

---

### Post by vnpifhf on 2011-02-19
because I need the windows 7 side for Adobe, but why does it think the disk is unknown, and why can't have the sliders!

---

### Post by oldfred on 2011-02-19
It may help to review some install examples with pictures so you understand the process better.


Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by vnpifhf on 2011-02-19
Yes I understand that is possible, but I need to get down to the problem of why ubuntu does nor give me the sliders or recognise the disk as we have 20-30 of the same laptops in the workplace and need to install 10.10 into all of them, and I don't have much time to do this!

Thank you.

---

### Post by 3177 on 2011-02-19
If i were you I would follow Janthonywj's steps to manually set up Ubuntu, then, if that doesnt work, delete an unnessecary partition of win7 and try again.

---

### Post by ubun2geek on 2011-02-19
u don't need to partition your disk, just use the wubi installer while in windows

---

### Post by vnpifhf on 2011-02-19
I do not want it in windows, but a separate operating system dual boot.

So is there no chance of finding out the problem, instead of using other things, because I think the installer in 10.10 is flawed.

---

### Post by oldfred on 2011-02-19
They have made the installer more difficult to use. But if you create partitions in advance and then use manual install it works just fine.

The advantage of creating partitions in advance is that you have total control over partitions including creating those that may not be part of the install like a shared NTFS partition.

---

### Post by vnpifhf on 2011-02-19
well I created 50GB of free space on win 7 and it does show up on the menu, I click on ext4 and use the \ as the root or whatever, it works, but then it says I have a faulty cd drive or a bad cd and it needs cleaning, as you can see in the attachment in my other post when I clearly don't, and why can't I have the easier slider option!

---

### Post by Brad55 on 2011-02-19
Ok what are you using to burn the cd's and if you are using a windows program to burn the cd make sure you use the slowest speed that you can, this might be your cd problem.

If I remember right a Primary partition can only have 4  partitions I think you will have to make a extended partition to put Ubuntu on.

---

### Post by vnpifhf on 2011-02-19
well I have a recovery partition, a system reserved partition and a windows 7 partition on 1 drive, and 50gb free space.

I had the same problem with 2 disks I have burned, so this disk I am using I had ordered from ubuntu, so this is not the problem.

---

### Post by Bölvaður on 2011-02-19
The error clearly states that there was an error while moving data from the cd to the hdd, Please tell me if this happens when the installer starts copying or if it is just somewhere in middle of copying.


> **OpenOffice.org said:**
> u don't need to partition your disk, just use the wubi installer while in windows

This will dual boot your computer using a virtual partition that is stored as a file on one of those windows partitions. When you have installed you will see a very ugly bootloader provided by the MS company and it will ask you if you want to boot up Windows7 or Ubuntu 10.10.

This should circumvent that i/o error.

Notice that you will not be able to access Ubuntu without restarting the computer, this is not a virtual machine!

[COLOR=Silver]
[COLOR=Black]> **Brad55 said:**
> Ok what are you using to burn the cd's and if you are using a windows program to burn the cd make sure you use the slowest speed that you can, this might be your cd problem.

If I remember right a Primary partition can only have 4  partitions I think you will have to make a extended partition to put Ubuntu on.[/COLOR] [/COLOR] [COLOR=Black]
It is possible that the data you are moving is corrupted because you dont use the slowest speed to burn the iso to an cd, or that the iso is corrupted.
Go on to check the checksum of the iso. Torrents are the best way to avoid corruption in my opinion. Then burn the cd on slowest possible settings.[/COLOR]

---

### Post by P.ap G on 2011-02-19
What puzzles me , is why install 10.10 which runs out in April 2012 ,as opposed to 10.04 (the LTS) which will last until April 2013 ,especially as it needs to be loaded on a fair number of computers . There  will be a bit of updating involved , but might it not be preferable to what you are going through now ?

 I'm no expert - just an idea . Hope I don,t get flamed for this.

---

### Post by uRock on 2011-02-19
> **P.ap G said:**
> What puzzles me , is why install 10.**0**4 which runs out in April 2012 ,as opposed to 10.**0**4 (the LTS) which will last until April 2013 ,especially as it needs to be loaded on a fair number of computers . There  will be a bit of updating involved , but might it not be preferable to what you are going through now ?

 I'm no expert - just an idea . Hope I don,t get flamed for this.
10.04 is the LTS, there isn't a non-LTS version of 10.04

---

### Post by VraiChevalier on 2011-02-19
Try the "Alternate Install" disk. Using the alternate install disk has worked for me before I ran into problems with the "Live" install disk and the graphical installer. Burn the disk at a slow burn (4x) and do the disk integrity check when you boot it.
[http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download](http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download)

---

### Post by vnpifhf on 2011-02-19
Yes thank you bolvaour! I have successfully installed ubuntu, I used the install boot command from wubi, and managed to install. But I wonder why there was no slider option.

I am refraining from creating a new thread because you guys are probably really busy on here, how do I get the trackpad working, because I have tried searching for it but it is really complicated and I do not understand... 

Its a sony vaio (specs on my sig) and I used the alps pointing driver in windows, it has a side and bottom scroll.

Thanks!

---

### Post by P.ap G on 2011-02-19
Whoops what a typo I meant 10.10 !
Many apologies.

---

### Post by ubun2geek on 2011-09-04
> **jahangir99 said:**
> I do not want it in windows, but a separate operating system dual boot.

So is there no chance of finding out the problem, instead of using other things, because I think the installer in 10.10 is flawed.

it will be a dual boot.

---

### Post by cmcanulty on 2011-09-04
Well the 1st screenshot shows you checked the box for use entire disk. To get the sliders you need to check set partitions manually.

---

