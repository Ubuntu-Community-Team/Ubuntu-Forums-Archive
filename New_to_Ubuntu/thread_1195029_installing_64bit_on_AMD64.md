---
title: "installing 64bit on AMD64"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-23
Hello, I installed ubuntu for a bit 3 years ago, just to see what it was like. Then I got a new pc and it wouldnt work with the display for some reason and I ve never got round to sorting the problem out. Well I ve got a new disply and getting really fed up with windows so I thought I d have another go.

I ve got 2x75gb drives, I thought Id put Ubuntu on the unused one, then boot from it and accees anything I need from Windows with Ubuntu. I ve tried burning the iso to a dvd but it wont boot from it. So I used wubi, as soon as I click on it I get an error message and whether I click on cancel, try again or ignore it makes that pining noise and nothing happened. In my frustration I just carried on clicking and to my surprise it started the installation process! I chose where to install it and clicked install and it went through loads of processes and got to "writing disc" and just hung in the same postion for 2 hours at which point I gave up. Any ideas? Its the 64bit version for the amd64 that I m trying to install. If I m using a seperate hd do I still need to partition? Thanks

---

### Post by sadaruwan12 on 2009-06-23
Well it's very hard to answer your question due to lack of info like to help you out we like to know the specification of your computer like the speed of your processor the brand stuff like that if you can plz post them after that we might be able to help you

---

### Post by typos1 on 2009-06-23
Ok, soz, its an Acer AspireT-180, XP Media Centre, 2000mhz dualcore AMDathlon64, 2GB of RAM (but windows only recognises 750mb)

---

### Post by sadaruwan12 on 2009-06-23
OK thx,
 First of all go to the site and get your self a new copy of the ISO file. You don't have burn it to a DVD use a CD 'cos all you need are in a compact CD I wonder why you've have used DVD for ubuntu and it seems to be a writing problem. So get fresh copy and try it from there and the RAM problem will get solved once you install Ubuntu 'cos mr.gates media center is full of bugs.

What ever you do you've to create partitions to setup your system even you use a new HDD. This user guide might help you [click here to go]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04").

---

### Post by LowSky on 2009-06-23
windows only sees 750 MB of your RAM... I would check on that, that seems very odd to me. Check your BIOS settings.

---

### Post by aeiah on 2009-06-23
whilst you're in your bios you might as well double-check that you've set the boot priority so it looks for a cd or dvd first before reading the harddrive.

also, try burning the iso to a cd, not a dvd (im assuming you're downloading the cd .iso of ubuntu which is approx 700mb in size)

---

### Post by typos1 on 2009-06-23
Thanks, used a dvd as I had run out of cds! Sorry, I forgot to say thtat the dvd didnt work so I used wubi and used a torrent to download the iso and put it straight on the hd

I checked the RAM before I installed and extra g and it was 750 despitsuppossedly having 1g as standard. I installed the extra g and it still says 750 mb!

---

### Post by sadaruwan12 on 2009-06-23
> **typos1 said:**
> Thanks, used a dvd as I had run out of cds! Sorry, I forgot to say thtat the dvd didnt work so I used wubi and used a torrent to download the iso and put it straight on the hd

I checked the RAM before I installed and extra g and it was 750 despitsuppossedly having 1g as standard. I installed the extra g and it still says 750 mb!

No worries it's Mr.Gates OS

---

### Post by typos1 on 2009-06-23
Yeah, I know! 

Should I reformat the second hd to NTFS? (the 1st drive with windows on is NTFS, the second FAT32)

I ve got a cd copy of 6.06 I got with a magazine a few years ago, should I use that and upgrade or do I have to totally re-install to upgrade anyway? Sorry baout all the questions!

---

### Post by Sef on 2009-06-23
> Should I reformat the second hd to NTFS? (the 1st drive with windows on is NTFS, the second FAT32)If you want to use the second hard drive as a home partition, then it is best to make it NTFS.  There is a program in add/remove that can read and write to it.  Just type in search: NTFS.  The NTFS configuration tool is the first choice.

> I ve got a cd copy of 6.06 I got with a magazine a few years ago, should I use that and upgrade or do I have to totally re-install to upgrade anyway? Sorry baout all the questions!If you did that, then you could update to 8.04 most likely.   There is no more support for the desktop for Dapper, but I don't think the repositories have been closed yet.

---

### Post by sadaruwan12 on 2009-06-23
> **typos1 said:**
> Yeah, I know! 

Should I reformat the second hd to NTFS? (the 1st drive with windows on is NTFS, the second FAT32)

I ve got a cd copy of 6.06 I got with a magazine a few years ago, should I use that and upgrade or do I have to totally re-install to upgrade anyway? Sorry baout all the questions!

Yo don't time travel just get a new one downloaded from the web(it's free and burn on to a CD or DVD( But with a CD ISO want burn successfully on a DVD this might have been your problem). The new version is full of new things and much more faster in response time so go for the new one. Also read the guide that I've given you 'cos NTFS and FAT is not Ubuntu's native file systems the native file system for Ubuntu is called ext and it has several versions the most effective once is ext3 but the new version is ext4 that is much more supported by the Ubuntu 9.04 jaunty so use that to partition your drive. Keep in mined that partitioning in Ubuntu is little different that in windows so it's better if you go through some tutorials first with out jumping right in.

---

### Post by typos1 on 2009-06-23
Ok. Tried dvd again and more sucessfull. I press f12 at boot up click on ubuntu and it gets to the partioning bit and says the partition is too small and to make it bigger but there is nothing that allows me to adjust as the installer is doing it, when I hit contuinue it goes to creating partiotion but it stayed at 0% for 10 mins so cancelled and booted from windows. Looks like I should buy some cds for the iso then. 

Just checked and the cd from the mag I ve got and its Kububtu NOT ububuntu as I thought! Its 6.06 and you boot from it, but I dont remember it creating partions

---

### Post by noenter1 on 2009-06-23
If you can wait you can always go to: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) to request a free cd. If you cant wait you can go to the store and buys some blank cds and burn the ISO to a disk. 

The difference between Ubuntu and Kubuntu is they use a different GUI(Graphical User Interface) and a few different applications, that do the same thing, but are made for that GUI. 

In order to install Ubuntu(or Kubuntu) you will have to format one of your hard drives(this will take place during installation). Make sure you don't have anything on you second hard drive and use that one. Leave your fist hard drive alone when you go through the installation process so you can still boot into either windows or Ubuntu. But remember to select your second hard drive when you install Ubuntu as it WILL need to reformat the hard drive you select and delete any data on it.

If you want to be able to exchange files while in either OS. You can partition a small amount of you second hard drive during installation as "FAT 32". It all depends on how much stuff you many or may not want to transfer. 5-10GB should be plenty. There are always ways to access the other OS partition while your on the other one(accessing windows while in Ubuntu, or Ubuntu while in windows), however there is a high risk or making that OS non-bootable that way, which is why its not preferred.

---

### Post by typos1 on 2009-06-23
Ok, I see thanks. Windows is NTFS, the 2nd drive is FAT32, so it will reformat it as ext so I dont have do it?

---

### Post by sadaruwan12 on 2009-06-23
> **typos1 said:**
> Ok, I see thanks. Windows is NTFS, the 2nd drive is FAT32, so it will reformat it as ext so I dont have do it?

Well when you create the partitions it'll be automatically selected so you don't have to do it.But you've to give ext file system you want is it EXT3 or EXT4 if you're using 9.04 then go with ext4 much faster than ext3.

---

### Post by typos1 on 2009-06-23
So when I boot from the cd it will do everything? It was trying to do this when I used the dvd and it said the partition was too small but I couldnt see anything that would allow me to adjsut the size/format etc. Or have I got to create the partitions before booting from the cd?

---

### Post by noenter1 on 2009-06-23
It should let you select and adjust the partitions and drives as you see fit.

---

### Post by NightwishFan on 2009-06-23
Remember to check the disk for errors. I do not know how to md5sum on Windows, however you can just reboot and check for errors. Good luck.

---

### Post by typos1 on 2009-06-23
Thanks, got a checksum prog on windows from the last time I tried Linux! 

So to confirm-it should let me adjust the partion size etc when booting from the disc?

---

### Post by noenter1 on 2009-06-23
Yes it will ask if you want to do a guided or custom partition, that's where you select what hard drive to use.

---

### Post by bodhi.zazen on 2009-06-23
> **Sef said:**
> If you want to use the second hard drive as a home partition, then it is best to make it NTFS.  There is a program in add/remove that can read and write to it.  Just type in search: NTFS.  The NTFS configuration tool is the first choice.

Just a small comment, although Linux (Ubuntu) can rw ntfs partitions, you can not use them as a /home partition as ntfs does not recognize permissions, and since not all files in /home have the same permissions, let alone users if you have more then one, you will have problems.

In terms of installation see :

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I agree with the other comments , I suspect there is something wrong with your RAM.

---

### Post by typos1 on 2009-06-23
Ok, I ll try again, but I m sure there was no option-it went ahead and did it itself and then said it was too small

---

### Post by typos1 on 2009-06-25
More success this time, used a cd and burnt it slowly. When I try and make a partition it says I need to have some swap space, then when I try and make 6gig of swap space it says that nothing can be done until the previous changes have been made-Shall I go ahead and after its done that I can make a partion for ubuntu?

Also theres a drop down box (cant remeber what its called now was couple of hours ago I tried it) but I can have the partition as blank or "/" or "/boot" or "/home" etc, do I want just "/" (the other drive is just "/"). 

According to uibuntu installer I have 3 drives as well! The 3rd being only 6 gb, but its news to me-I ve taken it apart before and there are only 2!

Will I be able to transfer my favourites and my email archive from firefox and office outlook?

Thanks

---

### Post by jimv on 2009-06-25
Just drop your computer into a box, fill the box with concrete, then throw that into a lake.  Revert to pen and paper.  The funny part is that this will still work about as well as Windows.

---

### Post by typos1 on 2009-06-25
Yeah, I think windows is pap as well, but thats no help in tryin ta get me linuxed up!

---

### Post by bodhi.zazen on 2009-06-25
Yes, when resizing partitions you sometime need to do it in steps.

Apply the first set of changes, then make a second set of changes.

6 Gb for swap seems excessive, unless you use hibernation I would thing 1 Gb more then enough. If you use hibernation swap = ram.

---

### Post by typos1 on 2009-06-25
Ok, thanks, what about the /, /boot, / home etc, which one do I need?

---

### Post by bodhi.zazen on 2009-06-25
You only need a swap and a / partition.

It is nice if you either make a separate /home or a data partition so you can keep your data separate from your OS.

---

### Post by typos1 on 2009-06-25
Done, I m posting using ububntu!

But how do I adjust the screen res?, I ve only goot 2 resolutions available-800x600 or 640x480, no widescreen options-help! 

And thanks for the help so far!

---

### Post by bodhi.zazen on 2009-06-25
Congrats :mrgreen:

I suggest a new thread as the install was a success, be sure to tell us what videocard you are using.

---

### Post by typos1 on 2009-06-25
Whhops, soz-willdo!

---

